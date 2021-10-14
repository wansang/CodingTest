            let graph: [String: [String]] = [
            "A" : ["B", "C"],
            "B" : ["A", "D", "E"],
            "C" : ["A", "F"],
            "D" : ["B"],
            "E" : ["B"],
            "F" : ["C"],
        ]
        
        print(self.DFS(arr: graph, start: "A"))
        self.recursiveDFS(arr: graph, start: "A")
        print(visited)
        
        print(self.BFS(arr: graph, start: "A"))
        
//    깊이 우선 탐색은 보통 한 개의 큐(Queue)와, 한 개의 스택(Stack)으로 구현함!!!!
//    방문 해야하는 노드를 저장하는 Stack(이하,needVisitStack)
//    이미 방문한 노드를 저장하는 Queue(이하, visitedQueue)
//    ① 탐색할 노드의 데이터를 needVisitStack에 넣는다
//    ② needVisitStack의 마지막 값을 추출해서(LIFO), visitedQueue에 해당 값이 존재하는지 확인한다
//    ③ 추출된 값이 visitedQueue에 존재하지 않으면, visitedQueue에 추가한다
//    ④ 추출된 값(방금 visitedQueue에 추가된 값)에 연결된 간선들을 모두 needVisitStack에 추가한다
//    needVisitStack이 빌 때까지 다시 ②번부터 반복함
    func DFS<T:Comparable & Hashable>(arr:[T: [T]],start:T)->[T]{
        var visited:[T] = []
        var stack:[T] = [start]

        while stack.isEmpty == false{
            let node = stack.removeLast()

            if visited.contains(node) == false{
                visited.append(node)
                stack.append(contentsOf: arr[node]!)
            }
        }

        return visited
    }
    
    var visited:[String] = []

    func recursiveDFS(arr:[String: [String]],start:String){
        print(start)
        if visited.contains(start){ return }
        
        visited.append(start)
        if let next = arr[start]{
            for i in 0..<next.count{
                recursiveDFS(arr: arr, start: next[i])
            }
        }
    }
    
//    너비 우선 탐색은 보통 두 개의 큐(Queue)로 구현함!!!!
//    방문 해야하는 노드를 저장하는 Queue(이하,needVisitQueue)
//    이미 방문한 노드를 저장하는 Queue(이하, visitedQueue)
//    이렇게 두 가지 큐로 구현할 수 있음!!
//    ① 탐색할 노드의 데이터를 needVisitQueue에 넣는다
//    ② needVisitQueue의 첫 번째 값을 추출해서(FIFO), visitedQueue에 해당 값이 존재하는지 확인한다
//    ③ 추출된 값이 visitedQueue에 존재하지 않으면, visitedQueue에 추가한다
//    ④ 추출된 값(방금 visitedQueue에 추가된 값)에 연결된 간선들을 모두 needVisitQueue에 추가한다
    
    func BFS<T:Comparable & Hashable>(arr:[T: [T]],start:T)->[T]{
        var visited:[T] = []
        var queue:[T] = [start]

        //["A", "B", "C", "D", "G", "H", "I", "E", "F", "J"]
        while queue.isEmpty == false{
            let node = queue.removeFirst()

            if visited.contains(node) == false{
                visited.append(node)
                queue.append(contentsOf: arr[node]!)
            }
        }

        return visited
    }

