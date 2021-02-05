---
layout: post
cover: 'assets/images/cover7.jpg'
navigation: True
title: Signed & Unsigned with Shuri & Scott
date: 2020-02-01 10:18:00
tags: Tech Shuri&Scott
subclass: 'post tag-tech tag-shuri&scott'
logo: 'assets/images/ghost.png'
author: mohitnnd
categories: mohitnnd
---

<p>A conversation between two friends about Signed & UnSigned Data Types.</p>
<p><b><em>Scott</em></b> - Heyy...I was solving one question and it stated - "Given an unsigned Int...", and now I am slightly confused. What is unsigned data type and how it's different from basic data type like Int?</p>
<p><b><em>Shuri</em></b> - Okay, In short, Signed Data Types will store both negative and positive values, whereas Unsigned Data Types will store only positive values.</p>
<p><b><em>Shuri</em></b> - To know how they differs in terms of range, lets start with a Bit.</p>
<p><b><em>Scott</em></b> - Okay, great.</p>
<p><b><em>Shuri</em></b> - A bit can store either value 0 or 1. That means 2 possible values.</p>
<table>
<tbody>
<tr>
<th>Bit1</th>
<th>Value</th>
</tr>
<tr>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>1</td>
<td>1</td>
</tr>
</tbody>
</table>
<p>2 bits can store 2 values(0 or 1) for each bit, that means we can represent or store 4 possible values with 2 bits.</p>
<table>
<tbody>
<tr>
<th>Bit1</th>
<th>Bit2</th>
<th>Value</th>
</tr>
<tr>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>1</td>
<td>0</td>
<td>2</td>
</tr>
<tr>
<td>1</td>
<td>1</td>
<td>3</td>
</tr>
</tbody>
</table>        
<p><b><em>Scott</em></b> - Okay, that means with Int2, we can represent 0, 1, 2 & 3. So, then the range  for Int2 will be [0, 3], right?</p>
<p><b><em>Shuri</em></b> - Umm...wrong. The range for Unsigned Int2 would be [0, 3],  not for a signed Int2.</p> 
<p><b><em>Shuri</em></b> - Signed Int will have both negative and positive values.</p> 
<p><b><em>Scott</em></b> - Okay..but how do we represent a negative value in bit? You can only represent 0 or 1 in a bit right? You can't put a -ve or +ve sign.</p>
<p><b><em>Shuri</em></b> - Correct, you can't put -ve or +ve sign. But, there are ways to represent a negative value.</p>
One way is to, invert the digits and add 1 to it. The resultant would represent its negative value.
Lets take 01 which represents 1.
<pre><code>
01 -> invert digits  -> 10 -> add 1 -> 11  
</code></pre>
Now, 11 represents -1.<br>
Btw, the above approach of inverting the digits and adding 1 to it is called 2's complement.
<p><b><em>Scott</em></b> - So, 11 which we used to represent 3 for unsigned Int2, can now now be used to represent -1 for signed Int2 right?</p>  
<p><b><em>Shuri</em></b> - That's correct.  And, 1 0 can be used to represent -2, since `2's complement` of 1 0 is 1 0.</p>
<p><b><em>Shuri</em></b> - This way with the same number of bits we can be used to represent both positive and negative values.
          Signed Int2 will have these values:</p>
<table>
<tbody>
<tr>
<th>Bit1</th>
<th>Bit2</th>
<th>Value</th>
</tr>
<tr>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>1</td>
<td>0</td>
<td>-2</td>
</tr>
<tr>
<td>1</td>
<td>1</td>
<td>-1</td>
</tr>
</tbody>
</table>       

<p><b><em>Scott</em></b> - Got it. Now if we look at signed Int2's range, it's `[-2, 1]`. It does not include 2 and 3 as we have used these to represent negative numbers, -2  & -1 respectively.</p>
<p><b><em>Shuri</em></b> - Exactly!</p>
<p><b><em>Scott</em></b>  - Okay...now what if I want to store 3 for a signed Int?</p>
<p><b><em>Shuri</em></b>  -  For a signed Int, we don't have space to store 3 with just 2 bits, as with 2 bits we can only store values till 1.<br> With 3 bits, you can store ranging from -4 to 3.</p>

<table>
<tbody>
<tr>
<th>Bit1</th>
<th>Bit2</th>
<th>Bit3</th>
<th>Value</th>
</tr>
<tr>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>0</td>
<td>1</td>
<td>0</td>
<td>2</td>
</tr>
<tr>
<td>0</td>
<td>1</td>
<td>1</td>
<td>3</td>
</tr>
<tr>
<td>1</td>
<td>0</td>
<td>0</td>
<td>-4</td>
</tr>
<tr>
<td>1</td>
<td>0</td>
<td>1</td>
<td>-3</td>
</tr>
<tr>
<td>1</td>
<td>1</td>
<td>0</td>
<td>-2</td>
</tr>
<tr>
<td>1</td>
<td>1</td>
<td>1</td>
<td>-1</td>
</tr>
</tbody>
</table> 

<p><b><em>Shuri</em></b> - Now if you see, we can actually come up with a formula for both signed and unsigned ranges.
For n bits, unsigned range would be <samp>[0, 2n - 1]</samp>, and for signed range it would be <samp>[-2n-1, 2n-1 - 1]</samp>.</p>
<p><b><em>Scott</em></b> - So, is it correct to say that signed data types reduces the range, as with unsigned we can represent more values?</p>
<p><b><em>Shuri</em></b> - I would not say it reduces the range, it actually shifts the range from positive values to negative values.</p>
<p><b><em>Scott</em></b> - Makes sense. Okay, I have one last question, when we declare just Integer (Int) as data type, is that unsigned or signed? And, how many bits it stores, because when we write Int we don't mention number of bits there?</p>
<p><b><em>Shuri</em></b> - Good question!! By default it's signed. To make it unsigned, we have to write UInt. And, how many bits it stores is dependent on the platform. On 32 bit platform, it behaves as Int32. On 64 bit platform, it behaves as Int64.</p>
Infact, this is clearly documented in Swift Documentation for Integer.
{% highlight swift %}
/// A signed integer value type.
///
/// On 32-bit platforms, `Int` is the same size as `Int32`, and
/// on 64-bit platforms, `Int` is the same size as `Int64`.
@frozen public struct Int : FixedWidthInteger, SignedInteger {
{% endhighlight %}

<p><b><em>Scott</em></b> - Noiceeee. Thanks Shuri🙂</p>
<p><b><em>Shuri</em></b> - Anytime 🙂 And, don't forget to check other Data Types and their range.</p>
<p><b><em>Scott</em></b> - Already on it... </p>