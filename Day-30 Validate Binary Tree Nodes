class Solution {
public:
    vector<int> parent;

    bool findParent(int n, vector<int>& leftChild, vector<int>& rightChild) {
        #pragma unroll
        for (int i=0; i < n; i++) {
            int left = leftChild[i], right=rightChild[i];
            if (left != -1) {
                if (parent[left]!=-1||left==i) {
                    return 0;
                }
                parent[left]=i;
            }
            if (right !=-1) {
                if (parent[right]!=-1||right==i) {
                    return 0;
                }
                parent[right]=i;
            }
        }
        return 1;
    }

    vector<int> root;

    int findRoot(int i) {
        if (parent[i]==-1) 
            return i;
        
        if (root[i]!=-1) return root[i];
        // Mark the node as visited during this call
        root[i]=-2; //for detecting cycle
        return root[i]=findRoot(parent[i]);
    }

    bool validateBinaryTreeNodes(int n, vector<int>& leftChild, vector<int>& rightChild)
    {
        parent.assign(n, -1);
        bool yes=findParent(n, leftChild, rightChild);
        if (!yes) return 0;

        root.assign(n, -1);
        int R0=findRoot(0);
        if (R0==-2||parent[R0]!=-1) return 0;
        #pragma unroll
        for (int i = 0; i<n; i++) {
            if (root[i]==-1) {
                int R=findRoot(i);
                if (R==-2||R!=R0||parent[R]!=-1) return 0;//Root shouldn't have a parent.
            }
        }
        return 1;
    }
};
