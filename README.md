# Codility Practice Questions Solved in Swift 

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

## CyclicRotation

```
public func solution(_ A : [Int], _ K : Int) -> [Int] {
    return rotatedArray(A, K)
}

func rotatedArray(_ A: [Int], _ K : Int) -> [Int] {

    //find array with empty slot for K places in the front

    if A.count <= 1 {
        return A
    }
    var clone = A
    var shifts = K

    if shifts > A.count {
        shifts = K % A.count
    }
    for i in shifts..<A.count {
        clone[i] = A[i-shifts]
    }
    for i in 0..<shifts {
        clone[i] = A[A.count - shifts + i] //A[5 - 1 - 2 + 0]
    }
    return clone
}
```

## Frog Jump

```
public func solution(_ X : Int, _ Y : Int, _ D : Int) -> Int {
    return jumps(X,Y,D)
}

func jumps(_ X: Int, _ Y: Int, _ D: Int) -> Int {

    let difference =  Y - X
    var jumps = difference / D
    let remainder = difference % D
    if remainder > 0 {
        jumps = jumps + 1
    }
    return jumps
}
```

## Missing Number 

```
public func solution(_ A : inout [Int]) -> Int {
    return missingElement(A)
}

func missingElement(_ arr: [Int]) -> Int {
    let totalSum = (arr.count + 1) * (arr.count + 2) / 2
    let sum = arr.reduce(0) { (sum, a) -> Int in
        return sum + a
    }

    return totalSum - sum
}

### TapeEquilibrium

```
public func solution(_ A : inout [Int]) -> Int {
    // write your code in Swift 4.2.1 (Linux)
    return findLeastDiff(A)
}
func findLeastDiff(_ a: [Int]) -> Int {
    if a.count < 2 {
        return 0
    }
    let totalSum = a.reduce(0) { (sum, a) -> Int in
        return sum + a
    }
    var sump1 = 0
    var sump2 = 0
    var leastDiff = Int.max
    var diff = Int.max
    for i in 0..<a.count - 1 {
        sump1 = sump1 + a[i]
        sump2 = totalSum - sump1
        diff = abs(sump1 - sump2)
        if diff == 0 {
            leastDiff = diff
            break
        }
        if diff < leastDiff {
            leastDiff = diff
        }
    }
    return leastDiff
}

```

