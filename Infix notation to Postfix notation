#include <iostream>
#include <string>
#include <stack>
using namespace std;

bool isOperator(char c){
    if(c == '+' || c == '-' || c == '*' || c == '/' || c == '%' || c == '^')
        return true;
    return false;
}

bool compare(char a, char b) {
    string low = "+-", high = "*/%";
    if ((low.find(a) != string::npos && low.find(b) != string::npos) ||
        (high.find(a) != string::npos && high.find(b) != string::npos) ||
        (low.find(a) != string::npos && high.find(b) != string::npos)) {
        return true; 
    }
    return false;
}

string postfix(string s){
    stack<char> st;
    string t;
    for(int i=0; i<s.size(); i++){
        if(s[i] >= '0' && s[i] <= '9') t += s[i];
        else if(s[i] == '(') st.push(s[i]);
        else if (s[i] == ')'){
            while(!st.empty() && st.top() != '('){
                t += st.top();
                st.pop();
            }
            if (!st.empty() && st.top() == '(') {
                st.pop(); 
            }
        }else{
            if(isOperator(s[i])){
                while(!st.empty() && compare(s[i], st.top())){
                    t += st.top();
                    st.pop();
                }
                st.push(s[i]);
            }
        }
    }
    while(!st.empty()){
        t += st.top();
        st.pop();
    }
    return t;
}

int main()
{
    string s;
    getline(cin, s);
    string t = postfix(s);
    cout << t;
    return 0;
}
