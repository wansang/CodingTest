//        Leo는 카펫을 사러 갔다가 아래 그림과 같이 중앙에는 노란색으로 칠해져 있고 테두리 1줄은 갈색으로 칠해져 있는 격자 모양 카펫을 봤습니다.
//        Leo는 집으로 돌아와서 아까 본 카펫의 노란색과 갈색으로 색칠된 격자의 개수는 기억했지만, 전체 카펫의 크기는 기억하지 못했습니다.
//        Leo가 본 카펫에서 갈색 격자의 수 brown, 노란색 격자의 수 yellow가 매개변수로 주어질 때 카펫의 가로, 세로 크기를 순서대로 배열에 담아 return 하도록 solution 함수를 작성해주세요.
//        제한사항
//        갈색 격자의 수 brown은 8 이상 5,000 이하인 자연수입니다.
//        노란색 격자의 수 yellow는 1 이상 2,000,000 이하인 자연수입니다.
//        카펫의 가로 길이는 세로 길이와 같거나, 세로 길이보다 깁니다. <= 이게 중요한 말 같음
//        입출력 예
//        brown    yellow    return
//        10    2    [4, 3]
//        8    1    [3, 3]
//        24    24    [8, 6]
        //모두다 사용해야 하는 거 구나
//        노란색이 하나 일때 n
//        필요한 브라운은 (n+2)*2 + n
        //16 + 8
        //가로 - 2
//        2,2,2,2,2,2,2,2
//        2,1,1,1,1,1,1,2
//        2,1,1,1,1,1,1,2
//        2,1,1,1,1,1,1,2
//        2,1,1,1,1,1,1,2
//        2,2,2,2,2,2,2,2
        
        //1의 가로가 1이면 세로는 23 그럼 브라운의 세로는 23 + 2
        
        print(self.solution(24, 24))
        
            func solution(_ brown:Int, _ yellow:Int) -> [Int] {
        var yellowH = 0 //yellow의 가로 길이
        
        for _ in 0..<yellow{
            yellowH += 1
            
            let yellowV = yellow / yellowH // 가로를 기준으로 세로를 구해 본다
            
            //1.총 필요한 brown의 갯수를 구해서 주어진 brown과 같다면
            let totalBrown = (yellowH * 2) + ((yellowV + 2) * 2)
            
            if totalBrown == brown{
                //카펫의 가로 길이는 세로 길이와 같거나, 세로 길이보다 깁니다
                let totalH = yellowH + 2 //전체 가로
                let totalV = yellowV + 2 //전체 세로
                if totalH == totalV || totalH > totalV{
                    return [totalH,totalV]
                }
            }
        }
        
        return []
    }

