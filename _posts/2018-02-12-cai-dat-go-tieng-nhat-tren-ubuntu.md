---
layout: single
title:  "Cách cài đặt gõ tiếng nhật trên ubuntu"
desc: "Cách cài đặt gõ tiếng nhật trên ubuntu"
excerpt: "Cách cài đặt gõ tiếng nhật trên ubuntu"
keywords: "japanese, ibus"
categories: [japan]
tag: [japan]
---

[Writing Japanese with Ubuntu 16.04 LTS Xenial Xerus](https://moritzmolch.com/2287)07/2016

  

**Update:** Instructions for Ubuntu 18.04 can be found [here](/2404).

This is a follow-up on the former articles "[Writing Japanese with Ubuntu 14.04 Trusty Tahr](/1453 "Writing Japanese with Ubuntu 14.04 Trusty Tahr")", "[Writing Japanese with Ubuntu 12.04 Precise Pangolin](/744 "Writing Japanese with Ubuntu 12.04 Precise Pangolin")" and "[Writing Japanese with Ubuntu 10.04 Lucid Lynx](/102 "Writing Japanese with Ubuntu 10.04 Lucid Lynx")".

Compared to Ubuntu 14.04 Trusty Tahr, setting up the Japanese input in Ubuntu again became simpler and better integrated. The default Japanese Input Method is now [**Mozc**](https://code.google.com/p/mozc/) (the open-source component of [Google's Japanese IME](http://www.google.co.jp/ime/), which is used in Android and Chrome OS) instead of [Anthy](https://en.wikipedia.org/wiki/Anthy) and I won't explain how to set up Anthy anymore since Mozc really works great.

The installation is actually very simple with one little stumbling stone which I will guide you over so you won't trip. So let's start:

1.  Because Mozc is not installed with the base-system, you have to install the Japanese language support first. Otherwise Mozc won't be available as input-method in the Text Entry settings. Additionally this will install some nice Japanese fonts and Japanese translations for Ubuntu if you ever want to use your System in Japanese. So let's begin by opening the **System Settings** and then the **Language Support**.  
    [![Screenshot-from-2014-03-28-062826.png](http://moritzmolch.com/wordpress/wp-content/uploads/2014/03/Screenshot-from-2014-03-28-062826.png)](http://moritzmolch.com/wordpress/wp-content/uploads/2014/03/Screenshot-from-2014-03-28-062826.png)

3.  If you get a message saying that the language support is not installed completely, you can either ignore it or let it install documentations and translations for the other installed languages on your system. In the Language Support-window, click on "**Install / Remove Languages...**".  
    [![Screenshot from 2014-03-28 06:32:01](http://moritzmolch.com/wordpress/wp-content/uploads/2014/03/Screenshot-from-2014-03-28-063201.png)](http://moritzmolch.com/wordpress/wp-content/uploads/2014/03/Screenshot-from-2014-03-28-063201.png)

5.  Scroll down or type "J" and **check the checkbox next to Japanese** in the "Installed"-column. After this, click on "**Apply Changes**".  
    [![Screenshot from 2014-03-28 06:32:19](http://moritzmolch.com/wordpress/wp-content/uploads/2014/03/Screenshot-from-2014-03-28-063219.png)](http://moritzmolch.com/wordpress/wp-content/uploads/2014/03/Screenshot-from-2014-03-28-063219.png)

7.  Next you have to **enter your password.**  
    [![Screenshot from 2014-03-28 06:32:45](http://moritzmolch.com/wordpress/wp-content/uploads/2014/03/Screenshot-from-2014-03-28-063245.png)](http://moritzmolch.com/wordpress/wp-content/uploads/2014/03/Screenshot-from-2014-03-28-063245.png)

9.  The necessary packages will now be downloaded and installed. Nothing to do for you in this step, but you can already start to save open documents and close unused windows in preparation for the next one. :-)  
    [![mozc_ibus4](http://moritzmolch.com/wordpress/wp-content/uploads/2016/07/mozc_ibus4.jpg)](http://moritzmolch.com/wordpress/wp-content/uploads/2016/07/mozc_ibus4.jpg)

11.  After the Japanese language support is installed, **you have to log out**. This is the small stumbling stone I mentioned before. For Mozc to show up in the list of input-methods, the session needs to be restarted. This is really kind of annoying but there's nothing you can do about that at this point. :-(

13.  Once you did a logout / login-cycle, open the **System Settings** and click on **Text Entry**.  
    [![Screenshot from 2014-03-28 06:29:52](http://moritzmolch.com/wordpress/wp-content/uploads/2014/03/Screenshot-from-2014-03-28-062952.png)](http://moritzmolch.com/wordpress/wp-content/uploads/2014/03/Screenshot-from-2014-03-28-062952.png)

15.  In the "Text Entry"-window, **click on the small Plus-sign** at the bottom of "Input sources to use".  
    [![Screenshot from 2014-03-28 06:30:17](http://moritzmolch.com/wordpress/wp-content/uploads/2014/03/Screenshot-from-2014-03-28-063017.png)](http://moritzmolch.com/wordpress/wp-content/uploads/2014/03/Screenshot-from-2014-03-28-063017.png)

17.  Select the entry "**Japanese (Mozc) (IBus)**" from the list and click on "**Add**".  
    [![mozc_ibus](http://moritzmolch.com/wordpress/wp-content/uploads/2016/07/mozc_ibus.jpg)](http://moritzmolch.com/wordpress/wp-content/uploads/2016/07/mozc_ibus.jpg)

19.  "Japanese (Mozc) (IBus)" should now show up inside the "Text Entry"-window and Mozc should be available in the menu-bar's menu. You probably want to change the setting "Use the same source for all windows" to "Allow different sources for each window" and switch to "New windows use the default source". Additionally you eventually want to reassign the key to switch to the next input source. I normally use the "Pause"-key to toggle between languages.  
    [![mozc_ibus1](http://moritzmolch.com/wordpress/wp-content/uploads/2016/07/mozc_ibus1.jpg)](http://moritzmolch.com/wordpress/wp-content/uploads/2016/07/mozc_ibus1.jpg)  
    [![mozc_ibus2](http://moritzmolch.com/wordpress/wp-content/uploads/2016/07/mozc_ibus2.jpg)](http://moritzmolch.com/wordpress/wp-content/uploads/2016/07/mozc_ibus2.jpg)

  

21.  Now fire up some text-editor and try it by clicking on "Mozc" in the text entry menu, set the input mode to hiragana and type some japanese. Switching between candidates is done by pressing the spacebar and katakana-conversion is done by pressing F7.  
    [![mozc_ibus3](http://moritzmolch.com/wordpress/wp-content/uploads/2016/07/mozc_ibus3.jpg)](http://moritzmolch.com/wordpress/wp-content/uploads/2016/07/mozc_ibus3.jpg)

I hope, this article answered all your first questions regarding Japanese input in Ubuntu.

If this article was useful to you, you might also be interested in my (short) [list of Japanese learning materials and software for Linux](/1646) and [how to type specific symbols and radicals in Mozc / Google’s Japanese IME](/2021).



<div style="text-align: right">Theo <a href="https://moritzmolch.com/2287">moritzmolch</a></div>
