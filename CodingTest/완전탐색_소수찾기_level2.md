//        한자리 숫자가 적힌 종이 조각이 흩어져있습니다. 흩어진 종이 조각을 붙여 소수를 몇 개 만들 수 있는지 알아내려 합니다.
//        각 종이 조각에 적힌 숫자가 적힌 문자열 numbers가 주어졌을 때, 종이 조각으로 만들 수 있는 소수가 몇 개인지 return 하도록 solution 함수를 완성해주세요.
//        제한사항
//        numbers는 길이 1 이상 7 이하인 문자열입니다.
//        numbers는 0~9까지 숫자만으로 이루어져 있습니다.
//        "013"은 0, 1, 3 숫자가 적힌 종이 조각이 흩어져있다는 의미입니다.
//        입출력 예
//        numbers    return
//        "17"    3
//        "011"    2
//        입출력 예 설명
//        예제 #1
//        [1, 7]으로는 소수 [7, 17, 71]를 만들 수 있습니다.
//        예제 #2
//        [0, 1, 1]으로는 소수 [11, 101]를 만들 수 있습니다.
//        11과 011은 같은 숫자로 취급합니다.
        print(self.solution("011"))

    var sol3Array : [Int] = []
    
    func solution(_ numbers:String) -> Int {
        let array = Array(numbers).map{ "\($0)" }
        
        let size = array.count
        var cnt = 0
        newDFS(size, array, 0, "")
        
        let setList = Array(Set(sol3Array))
        
        for element in setList{
            if isPrime(num:element) {
                cnt += 1
            }
        }
        
        return cnt
    }
    
    func newDFS(_ size: Int, _ numbers : [String], _ depth : Int, _ value : String){
        var tempNumbers = numbers
        
        if size > depth {
            for i in 0..<numbers.count{
                let item = tempNumbers[i]
                tempNumbers.remove(at: i)
                sol3Array.append(Int(value + item)!)
                newDFS(size, tempNumbers, depth + 1, value + item)
                tempNumbers.insert(item, at: i)
            }
        }else{
            print(value)
        }
    }
    
    func isPrime(num: Int) -> Bool {
        var result: Bool = true
        
        if num < 2 {
            result = false
        }else if num > 2 {
            for i in 2..<num {
                if num%i == 0 {
                    result = false
                }
            }
        }
        return result
    }
