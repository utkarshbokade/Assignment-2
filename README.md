Convert numbers to Ordinal words Algorithm
step1: create a function NumToOrw with pararmeters number and output
step2: inside the function create an if statement such that if the number is 0 
the result will be "zeroth"
step3: create 4 arrays such that 
array1 contains all numbers from 1 to 9 in words 
array2 contains all numbers multiple of 10  from 10 to 90 in words 
array3 contains all numbers from 1 to 9 in ordinal words 
array4 contains all numbers multiple of 10 from 10 to 90 in ordinal words
step4: create nested if statement such that if number is modulo divisible by 10 the digit is in ones place and so on
step5: create nested if statements such that if the digit is in hundreds place output the digit from array1 and 2 followed by the word hundred and 
so on for thousands, millions etc
step6: create an if statement such that if the digit is in tens places and the digit in 0nes place is zero 
output the coressponding value from array3
else if the digit in ones place is not zero and the digit at tens place is a non zero output
the coressponding value from array2 and 4
step7: return return output 
step8: take the input for parameter number from the user and call the function NumToOrw
print the entered number and the output.






 
 
 
 <?php
function fullWordOrdinal($number) {
    if (empty($number[0])) 
    {
       $out = "zeroth";
    }
     $ord1 = array( 1=> "first", 2 => "second", 3 => "third", 5 => "fifth",8 => "eighth", 9 => "ninth", 11 => " eleventh", 12 => " twelfth", 13 => " thirteenth", 14 => " fourteenth", 15 => " fifteenth", 16 => " sixteenth", 17 => " seventeenth", 18 => " eighteenth", 19 => " nineteenth");
    $num1 = array("one","one", "two", "three", "four", "five", "six", "seven", "eight", " nine", " ten", "eleven", " twelve", " thirteen", " fourteen", "fifteen", " sixteen", " seventeen", " eightteen", " nineteen");
    $num10 = array(""," ten", " twenty", " thirty", " fourty", " fifty", " sixty", " seventy", " eighty", " ninety");
    $places = array(2 => "hundred","thousand", 6 => "million", 9 => "billion", 12 => "trillion", 15 => "quadrillion", 18 => "quintillion", 21 => "sextillion", 24 => "septillion", 27 => "octillion");
    
    $number = array_reverse(str_split($number));
  if ($number[0]== 0) {
        if ($number[1] >= 2)
            $out = str_replace("y", "ieth", $num10[$number[1]]);
        else
            $out = $num10[$number[1]]."th";
    } else if ($number[1] == 1) {
        $out = $ord1[$number[1] . $number[0]];
    } else {	
        if (array_key_exists($number[0], $ord1))
            $out = $ord1[$number[0]];
        else
            $out = $num1[$number[0]]."th";
    }
        
    if($number[0] == 0 || $number[1] == 1){
        $i = 2;
    } else {
        $i = 1;
    }
    
    while ($i < count($number)) {
        if ($i == 1) {
            $out = $num10[$number[$i]] . " " . $out;
            $i++;
        } else if ($i == 2) {
            $out = $num1[$number[$i]] . " hundred" . $out;	
            $i++;
        } else {
            if (isset($number[$i + 2])) {
                $tmp = $num1[$number[$i + 2]] . " hundred ";
                $tmpnum = $number[$i + 1].$number[$i];
                if ($tmpnum < 20)
                    $tmp .= $num1[$tmpnum] . " " . $places[$i] . " ";
                else 
                    $tmp .= $num10[$number[$i + 1]] . " " . $num1[$number[$i]] . " " . $places[$i] . " ";
                
                $out = $tmp . $out;
                $i+=3;
            } else if (isset($number[$i + 1])) {
                $tmpnum = $number[$i + 1].$number[$i];
                if ($tmpnum < 20)
                    $out = $num1[$tmpnum] . " " . $places[$i] . " " . $out;
                else 
                    $out = $num10[$number[$i + 1]] . " " . $num1[$number[$i]] . " " . $places[$i] . " " . $out;
                $i+=2;
            } else {
                $out = $num1[$number[$i]] . " " . $places[$i] . " " . $out;
                $i++;
            }
        }
    }
 if (empty($number)) 
    {
        $out = "zeroth";
    }
    return $out;
}
$number= (int)readline('Enter a number: ');
echo  ("Entered number is ".$number) ;
echo "   ";
 echo fullWordOrdinal($number)
 ?> 
