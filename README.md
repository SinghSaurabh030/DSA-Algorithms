### Sieve
```
    	bool sieve[1000001];
   ll N=1000000;
     for(ll i=1 ; i<=N ; i++){
          sieve[i]=true;
     }
     for(ll i=2 ; i*i<=N ; i++){
          if(sieve[i]==true){
               for(ll j=i*i ; j<=N ; j+=i){
                    sieve[j]=false;
               }
          }
     }

```

### Disjoint Set
```
    class DisjointSet{
        vector<int>rank,parent;
        public:
        DisjointSet(int n){
            rank.resize(n+1,0);
            parent.resize(n+1);
            for(int i=0 ; i<=n ; i++) {
                parent[i]=i;
            }
        }

            int findParent(int node){
                if(parent[node]==node){
                    return node;
                }
                return parent[node]=findParent(parent[node]);
            }

            void unionByRank(int u,int v){
               int ulp_v=findParent(v);
               int ulp_u=findParent(u);
               if(ulp_v==ulp_u){
                    return;
               }
               else if(rank[ulp_v]<rank[ulp_u]){
                    parent[ulp_v]=ulp_u;
               }
               else if(rank[ulp_u]<rank[ulp_v]){
                    parent[ulp_u]=ulp_v;
               }
               else{
                    parent[ulp_u]=ulp_v;
                    rank[ulp_v]++;
               }

            }
        
    };

```