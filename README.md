# Codility Practice Question Solved in Swift 

## Binary Gap

``` 
func solution(_ num: Int) -> Int {
    return getBinaryString(num)
}

func getBinaryString(_ N: Int) -> (String, Int) {
    var num = N
    var string = ""
    var previousNumber = -1
    var lastCount = 0
    var counter = 0
    while num  > 0 {
        let remainder = num % 2
        if previousNumber == 1 && remainder == 0 {
            counter += 1
        } else {
            //reset count
            if counter > lastCount {
                lastCount = counter
            }
            counter = 0
            previousNumber = remainder
        }
        string = "\(remainder)" + string
        num = num / 2
    }
    return (string, lastCount)
}
```

## OddOccurrencesInArray 

```
func solution(_ A: [Int]) -> Int {
    return findOdd(A) 
}

func findOdd(_ A : [Int]) -> Int{
    var i = 0
    var oddNum:Int?
    if A.count == 1 {
        return A[0]
    }
    let sortedArray = A.sorted()
    while(i <= sortedArray.count - 2){
        let item0 = sortedArray[i]
        let item1 = sortedArray[i+1]
        print(item0)
        print(item1)
        if item0 == item1 {
            i += 2

        } else {
            oddNum = item0
            break
        }
    }
    if i == sortedArray.count - 1 {
        oddNum = sortedArray[i]
    }

    return oddNum!
}
```

