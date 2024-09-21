def int_to_words(n):
    ones = ['zero', 'one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine']
    teens = ['ten', 'eleven', 'twelve', 'thirteen', 'fourteen', 'fifteen', 'sixteen', 'seventeen', 'eighteen', 'nineteen']
    tens = ['', '', 'twenty', 'thirty', 'forty', 'fifty', 'sixty', 'seventy', 'eighty', 'ninety']
    thousands = ['', 'thousand', 'million', 'billion']

    def helper(num):
        if num < 10:
            return ones[num]
        elif num < 20:
            return teens[num-10]
        elif num < 100:
            return tens[num//10] + ('' if num%10==0 else ' ' + helper(num%10))
        elif num < 1000:
            return ones[num//100] + ' hundred' + ('' if num%100==0 else ' and ' + helper(num%100))

    result = ''
    i = 0
    while n > 0:
        if n % 1000 != 0:
            result = helper(n%1000) + ' ' + thousands[i] + ('' if result=='' else ' ') + result
        n //= 1000
        i += 1
    return result.strip()

# Test the function
print(int_to_words(1000))  # Output: one thousand
print(int_to_words(4003))  # Output: four thousand three
