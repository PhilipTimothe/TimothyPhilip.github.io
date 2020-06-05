---
layout: post
title:      "Conditional or Not To Conditional"
date:       2020-06-05 01:43:48 +0000
permalink:  conditional_or_not_to_conditional
---

### The process ?

Throuhout the process of building out a command line interface I came across challenges that I was able to overcome.  Some challenges where easily achievable a others made me want to curl up in a ball and cry.  In particular, conditionals and the use there of, were the bain on my existenance at certain periods throughout the process of building out my cli.  Other than that the process was relatively exciting because I found myself learning what it really took to get through a code build.  Most of all, I got to prove to myself that I could hack it enough to get through to the next checkpoint.  

### Conditional Codes in my CLI

```
def valid?(num_id)
        num = num_id.to_i
        if num < 1 || num > Museum.all.size
            puts "So sorry, that is not a valid choice."
            puts "Please enter a valid number from list."
            sleep 0.5
            main_functions 
        end
        return num
    end
```

I found myself asking the question, why do I need this conditional, but I understood that it was essential in order to get to the next phase of user ability.  The code above is a code that validates an input.  Sounds simple right?  Well not exactly.  During the process it work well for the purposes of getting full completion of the program from start to finish.  Then there was a catch.  The program would run but it would end up with a glitch if I try to perform the conditional.  If the code looked to validate the input it would somehow hold on to the original request and try to complete the full program run while running the current requested operation.   It was like it was doing two things at once.  

### When all else fails ask for help !

I ran up against a brick wall trying to understand where I was going wrong.  I just didn't know.  So I asked so many questions and got a ton of help.  At times it felt somewhat embarrassing but I realize that the only way I would ever get out from under was to put all pride aside and ask the really dumb questions, so I did.  With the feeback I was able to implement a while loop to clean up a portion of my code:

```
def run
        
        sleep 1
        welcome_guest
        Api.enter_museum
        main_functions
        
        input = ""
        while input != "n"
        input = gets.strip
        # binding.pry
            case input
                when "y"
                    main_functions
                when "n"
                    puts ""
                    puts "Dont forget, art makes life fun!!!  See you next time  =)"  
                    break
                when "\n"
                    break
                else
                    puts "Sorry, we do not understand."
                    explore_more?
            end
        end
    end
```

### Figuring it all out

With the provided advice I was able to understand a bit more about what might be going wrong.  Since I was trying to do a lot, I had to work out that I would need to first simplify things to get the desired result.  I abstracted the code I wrote to a much simplier position.  I allowed to realize that the only thing that was incorrect with the code was the implementation of the condition.  I ended having to target a condition in the one place that I didnt think I would need one, which was my main functions method.  

```
def main_functions
        print_all_art_departments
        print_selection_prompt
        input = gets.chomp 
        if valid?(input) 
            @art_dep_choice = input.to_i
            get_department_items
            print_second_selection_prompt
            input = gets.chomp
            if valid?(input)
                @artwork_choice = input.to_i
                details = get_artwork_details
                print_selection_details(details)
                explore_more?
            else
                puts ""
                puts "So sorry, that is not a valid choice."
                puts "Lets start again!"
                sleep 1
                main_functions
            end
        else
            puts "So sorry, that is not a valid choice."
            puts "Please enter a valid number from list."
            sleep 0.5
            main_functions
        end
    end
```

### In the end

In the end I still didnt do what I truly intended to do but the desired result was achieved and the learning curve was the best thing I could have hoped for.



