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
