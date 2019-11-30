Updating the Website to Christmas 2019
======================================

The easiest part to update at first will be the html files. I'll do that now, keeping a list of what I need to modify.

Modifying the html Files
------------------------

Here is my list:

+-----------------------+---------------------------------------------------------------------------------------+
| header.html           | Changed the main heading to Christmas 2019                                            |
+-----------------------+---------------------------------------------------------------------------------------+
| footer.html           | Changed the footer message to Merry Christmas 2019, eliminating the                   |
|                       | <span>id="year"</span> that was there to insert the current year.                     |
+-----------------------+---------------------------------------------------------------------------------------+
| base.html             | Changed the block title to Christmas 2019                                             |
+-----------------------+---------------------------------------------------------------------------------------+
| giftlist.html         | Updated the welcome messages (one for small screens -- do I really need two?)         |
+-----------------------+---------------------------------------------------------------------------------------+

Saving to Github
----------------

It is important to be able to keep my files current between my two main places for working on the program. I use Git and
Github for that.

I created a new repository, christmas19, on github. I enabled version control in PyCharm then did my first commit,
remembering this time, to remove secrets.json from the commit.

