//# xiaoding
//dijsktra 
#include <bits/stdc++.h>
using namespace std;
using ll=long long;
const ll INF=1e18;
int main(){
	ios_base::sync_with_stdio(false);
	cin.tie(0);
    int n,m;ll s;cin>>n>>m>>s;
    vector<vector<pair<int,ll>>> g(n+1);
    while(m--){
        int u,v;ll w;cin>>u>>v>>w;
        g[u].push_back({v,w});
    }
    vector<ll> dist(n+1,INF);dist[s]=0;
priority_queue<pair<ll,int>,vector<pair<ll,int>>,greater<pair<ll,int>>> pq;pq.push({0,s});
    while(!pq.empty()){
        auto [d,u]=pq.top();pq.pop();
        if(d!=dist[u]) continue;//lazy delete
        for(auto e:g[u]){
            int v=e.first;
            ll w=e.second;
            if(d+w<dist[v]){
                dist[v]=d+w;
                pq.push({dist[v],v});
            }
        }
    }
    for(int i=1;i<=n;i++) cout<<dist[i]<<(i==n?'\n':' ');
	return 0;
}
