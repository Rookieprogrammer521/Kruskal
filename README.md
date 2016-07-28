import sys

def kruskal(graph):
    k=1
    i=0
    #Initialize the necessary arrays
    tree = [[0 for i in range(0,len(graph))] for j in range(0,len(graph))]
    p = [0 for i in range(0,len(graph))]
    #"Every tree belongs to itself"
    while(i<len(graph)):
        p[i]=i
        i+=1
    #While k < vertex-1
    while(k<len(graph)):
        #"min" will be a very high value
        min = sys.maxsize
        #Find the min value in all graph
        for i, value in enumerate(graph):
            for j, value2 in enumerate(graph[i]):
                if value2 != 0 and value2 < min and p[i] != p[j]:
                    min = value2
                    Node1 = i
                    Node2 = j
        temp = Node2
        tree[Node1][Node2] = min
        p[Node2] = Node1
        for i in p:
            if i == temp:
                i = Node1
        k+=1
    #Return the tree
    return tree

if __name__ == '__main__':
    tree = []
    print("Hi, Kruskal desu!")
    size = int(input("graph size: "))
    m_graph = [[0 for i in range(0,size)] for j in range(0,size)]
    for i in range(0,size):
        for j in range(0,size):
            m_graph[i][j] = int(input())
    tree = kruskal(m_graph)
    for i in tree:
        print(i)

