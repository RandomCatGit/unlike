# unlike
A simple script automation to remove all pages and groups from your facebook liked list.

## Disclaimer

The following code is given to the public for useage limited to simplyfying the process of disliking/unsubscribing from a plathora of pages that were unknowingly subscribed to and now the user's timeline is filled with unrelated/misleading/annoying content who wish to dislike them as a bulk. Using this script, ALL YOUR LIKED/SUBSCRIBED PAGES AND GROUPS WILL GET REMOVED without controlled operation. I am not responsible and in any case will not be responsible for any damage/loss or any such things that may come out of execuring this script whatsoever. Run it at your own discretion.

You will need a fast internet connection and fast computer for this to work effectively. If not, adjust the timeout parameter in the code.

<b>To unlike pages</b>, go to your liked pages list page: <pre>https://www.facebook.com/[YourUserID]/likes</pre>

Run the following script in the console of your browser. (Pressing Ctrl + Shift + I opens it) (And if you're using Mac, get a PC.)

<pre>function unLike(bool) {
  try {
    setTimeout(function() {
      document.getElementsByClassName('_52nf')[0].click(); // clicked first liked button
      setTimeout(function() {
        var b = document.getElementsByClassName('uiContextualLayerBelowLeft');
        if (b === undefined) {
          c = document.getElementsByClassName('InterestListMenuDisconnect')[0].getElementsByTagName('span')[0];
        }
        if (b === undefined && c === undefined) {
          console.log('need timeout check');
        }
        if (b === undefined) {
          document.getElementsByClassName('InterestListMenuDisconnect')[0].getElementsByTagName('span')[0].click(); // the other one doesn't work
        } else {
          b[b.length - 1].getElementsByTagName('span')[0].click(); // unlike click
        }
        if (document.getElementsByClassName('_52nf').length > 0) {
          if (bool) {
            document.scrollingElement.scrollTop += 114;
          }
          unLike(!bool);
        }
      }, 1000);
    }, 300);
  } catch (ex) {
    setTimeout(function() {
      unLike(bool);
    }, 2000);
  }
}
unLike(false);</pre>

<b>To unlike groups</b>, go to your liked groups list page: <pre>https://www.facebook.com/[YourUserID]/groups</pre>

Run the following script in the console of your browser.
  
<pre>document.getElementsByClassName('sp_2pJbEEL4hXl_1_5x sx_726cb7')[0].click();
document.getElementsByClassName('_2ieq')[1].click();
setTimeout(function() {
	document.getElementsByClassName('groupsLeaveButton')[0].click();
}, 1500); // timeout between confirmation dialog popup</pre>

The page gets refreshed everytime you leave a group so you need to press up and enter after the page is refreshed to execute the last snippet executed. I automated that process as well in Java. This cannot be run in browser console and requires a Java Environment/JVM to run. If you're a developer, you know what to do. I leave the code below:

<pre>/**
 * A simple Robot execution in Java for pressing up and enter key with a specific timeout
 */
package com.CodeLab;

import java.awt.AWTException;
import java.awt.Robot;
import java.awt.event.KeyEvent;

/**
 * 
 * Keypresser is 
 *
 * @author RandomCatGit
 */
public class Keypresser {
	
	private static Robot r;
	public static void main(String[] args) throws AWTException, InterruptedException {
		r = new Robot();
		Thread.sleep(2000);
		callRecc();
	}
	/**
	 * callRecc method is used for 
	 * @throws InterruptedException 
	 * 
	 */
	private static void callRecc() throws InterruptedException {
		r.keyPress(KeyEvent.VK_UP);
		
		r.keyPress(KeyEvent.VK_ENTER);
		Thread.sleep(6000); // timeout between reloads
		callRecc();
	}

}</pre>
