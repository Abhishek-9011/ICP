problem 1325:

Approach: First we do a dfs preorder then when we reach leaf node we check if it is equal to target we return null so it will no get connected and get deleted and if the value if not equal to target the we connect it with its parent node and by return it

code:
class Solution {
public TreeNode removeLeafNodes(TreeNode root, int target) {
if(root!=null){
root.left = removeLeafNodes(root.left,target);
root.right = removeLeafNodes(root.right,target);
if(root.val==target && root.left==null && root.right==null){
return null;
}
return root;
}
return null;
}
}

problem 2673

apporach:
We use DFS in postorder starting from the root (index 0). For each node, we recursively calculate the path cost of its left and right subtrees. If both costs are different, we add the absolute difference to ans to balance the paths. Then we return the current node cost plus the maximum of left and right subtree cost. This ensures all root-to-leaf paths become equal with minimum increments.

code:
class Solution {
public int ans;
`
    public int minIncrements(int n, int[] cost) {
        dfs(0, cost);
        return ans;
    }

    public int dfs(int i, int[] cost) {
        if (i >= cost.length)
            return 0;
        int a = dfs(2 * i + 1, cost);
        int b = dfs(2 * i + 2, cost);
        ans += Math.abs(a - b);
        return cost[i] + Math.max(a, b);
    }

}
