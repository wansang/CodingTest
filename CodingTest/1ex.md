//        1    6개 번호가 모두 일치
//        2    5개 번호가 일치
//        3    4개 번호가 일치
//        4    3개 번호가 일치
//        5    2개 번호가 일치
//        6(낙첨)    그 외
        
//        lottos    win_nums    result
//        [44, 1, 0, 0, 31, 25]    [31, 10, 45, 1, 6, 19]    [3, 5]
//        [0, 0, 0, 0, 0, 0]    [38, 19, 20, 40, 15, 25]    [1, 6]
//        [45, 4, 35, 20, 3, 9]    [20, 9, 3, 45, 4, 35]    [1, 1]
        
//        입력값 〉    [0, 0, 0, 0, 0, 0], [38, 19, 20, 40, 15, 25]
//        기댓값 〉    [1, 6]
//
//        입력값 〉    [45, 4, 35, 20, 3, 9], [20, 9, 3, 45, 4, 35]
//        기댓값 〉    [1, 1]
        
        // Do any additional setup after loading the view.
        print(self.solution([45, 4, 35, 20, 3, 9], [20, 9, 3, 45, 4, 35]))


//    func solution(_ lottos:[Int], _ win_nums:[Int]) -> [Int] {
//
//        let zeroCount = lottos.filter { $0 == 0}.count
//        let winCount: Int = win_nums.filter { lottos.contains($0) }.count
//
//
//        return [min(7-winCount-zeroCount,6), min(7-winCount,6)]
//    }
    
//    func solution(_ lottos:[Int], _ win_nums:[Int]) -> [Int] {
//        var topScore:Int = 0
//        var lowScore:Int = 0
//        var selectNumberCount:Int = 0
//
//        //최고 등수는 현재 내꺼의 0의 갯수 와 맞은 당첨 번호의 합 갯수
//        //최하 등수는 내꺼중에 맞은 번호의 갯수
//
//        let nonZeroArr = lottos.filter{ $0 != 0 }
//
//        nonZeroArr.forEach { myNumber in
//            win_nums.forEach { winNumber in
//                if myNumber == winNumber{
//                    selectNumberCount += 1
//                }
//            }
//        }
//
//        let top = ( 6 - nonZeroArr.count ) + selectNumberCount
//
//        if top == 6{
//            topScore = 1
//        }else if top == 5{
//            topScore = 2
//        }else if top == 4{
//            topScore = 3
//        }else if top == 3{
//            topScore = 4
//        }else if top == 2{
//            topScore = 5
//        }else{
//            topScore = 6
//        }
//
//        if selectNumberCount == 6{
//            lowScore = 1
//        }else if selectNumberCount == 5{
//            lowScore = 2
//        }else if selectNumberCount == 4{
//            lowScore = 3
//        }else if selectNumberCount == 3{
//            lowScore = 4
//        }else if selectNumberCount == 2{
//            lowScore = 5
//        }else{
//            lowScore = 6
//        }
//
//        return [topScore,lowScore]
//    }


