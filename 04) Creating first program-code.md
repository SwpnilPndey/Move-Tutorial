## Sample program to add two numbers 

module myAddr:example {
    useaptos_std::debug;
    use std::signer;

    public fun adding(a:u8,b:u8):u8 {
        return (a+b);
    }
}

## Explanation