# luogu_problem p5587
a problem solution repository
#include <iostream>
#include <string>
#include <vector>
using namespace std;
string process(const string&s){
    string res;
    for(char c:s){
        if(c=='<'){
            if(!res.empty())res.pop_back();
        }else{
            res.push_back(c);
        }
    }
    return res;
}
int main() {
    vector<string> modle,ans;
    string line;
    while(getline(cin,line)&&line!="EOF"){
        modle.push_back(process(line));
    }
    while(getline(cin,line)&&line!="EOF"){
        ans.push_back(process(line));
    }
    int count{0};
    int m=min(modle.size(),ans.size());
    for(int i=0;i<m;i++){
        int mi=min(modle[i].size(),ans[i].size());
        for(int j=0;j<mi;j++){
            if(modle[i][j]==ans[i][j])count++;
        }
    }
    int t;
    cin>>t;
    double kpm=(double)count/t*60;
    printf("%.0lf\n",kpm);
    getchar();
    getchar();
    return 0;
}
