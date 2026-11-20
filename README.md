# lucban_noel_b_2D-problem-1.py
This code is for my assignment on DSA
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None


def build_tree():
    root = Node(15)
    root.left = Node(10)
    root.right = Node(25)
    root.left.left = Node(4)
    root.left.right = Node(12)
    root.right.left = Node(20)
    root.right.right = Node(30)
    root.left.left.left = Node(2)
    root.left.left.right = Node(6)
    return root


def inorder(node):
    if node is None:
        return []
    return inorder(node.left) + [node.value] + inorder(node.right)


def preorder(node):
    if node is None:
        return []
    return [node.value] + preorder(node.left) + preorder(node.right)


def postorder(node):
    if node is None:
        return []
    return postorder(node.left) + postorder(node.right) + [node.value]


def level_order(root):
    if root is None:
        return []

    result = []
    queue = [root]
    front = 0

    while front < len(queue):
        current = queue[front]
        front += 1
        result.append(current.value)

        if current.left is not None:
            queue.append(current.left)
        if current.right is not None:
            queue.append(current.right)

    return result


if __name__ == "__main__":
    root = build_tree()
    print("Inorder:  ", *inorder(root))
    print("Preorder: ", *preorder(root))
    print("Postorder:", *postorder(root))
    print("Level-order:", *level_order(root))
    
