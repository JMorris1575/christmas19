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

I copy/pasted the .gitignore file from Christmas2018 and updated the c18 to c19 in the lines that contained it.

After committing the .gitignore file I did a Git/Push in PyCharm to send the current version of the website to
github.

Updating the Images
-------------------

Another thing I need to update is the new images and then do another l * o * n * g push to github. I should be able to
copy/paste the images from this computer (my home computer) to the PyCharm's project directory and then do another push.

Problems Saving the Images
++++++++++++++++++++++++++

I created some problems for myself in the process. First, I did the push with last year's gift images. Since it was
taking a long time, and since I had to leave Kalamazoo soon, I cancelled the push part way through and then copied this
year's gift images and did the push again.

It didn't take. Github had many of the old images still. I guess that Git goes by the filename and location rather than
the contents of .png files. Also, some of the image files were labeled ``gift #.png`` instead of ``Gift #.png``.

After some thrashing around trying to rename files in the project directory and pushing them again and other failed
attempts, I finally deleted all the gift image files from the project directory, did a commit and then a push of the
project without gift images, then reloaded the renamed images from the Pictures folder in Kalamazoo, did a commit and
then a push of the reconstituted project and it worked!

Cloning the Project to the Rectory Computer
-------------------------------------------

Following the directions in **Instructions**, I was able to clone the project here to my rectory computer. It was not
assigned to any virtual environment. When I got into Settings/Project Interpreter, I was able to find the christmas19
environment and attached to that. PyCharm now opens the project in the christmas19 environment.

I pip installed sphinx, django and psycopg2 without incident and used TeamViewer to transfer secrets.json to this
computer.

Running the server (``python manage.py runserver``) and checking the local website confirmed that everything is working
as expected -- although, for some reason, all of the gifts are marked as wrapped in spite of also being marked as having
been selected.

Creating the 2019 Development Database
--------------------------------------

As explained in **Instructions**, I got into pgAdmin4 and created a database I called c19. I had to do a
``python manage.py migrate`` before it would work, and then I copied the users from 2018 to this year's database
with ``python manage.py dumpdata auth.user > c18Users.json`` and copied c18Users.json to the Christmas 2019 project.

I allowed it to put it into Git but then had second thoughts since everybody's email addresses are in there in plain
text. After doing the ``python manage.py loaddata c18Users.json`` I moved the json file to One Drive to be used again.

But now I have second thoughts about that. I've already added Joey to the user list so I should just create a new json
file with him in it to do the transfer.

Anyway, it all seems to be working.

Updating the Content
--------------------

The gift list went in today (2019-12-02) without much problem. For a while I had two Gift 1s because I mistyped 13, but
I was able to clear that up easily enough.

Moving Back to the Home Computer
--------------------------------

I had accidentally started my Christmas2019 project in the ``Documents/PyCharmProjects`` directory instead of the
``Documents/MyDjangoProjects`` directory. I copied it from the former to the latter, started it up, and it seems to be
working fine. I did a Git->Pull and updated the program -- mostly this file I think. Now I will create a c19 database
on this computer and populate it with the data in ``2019-12-03-user-gift.json`` To get these two computers to match.

I completed the above and now all 36 new gifts are showing.

But - Oops! - I did the loaddata into the c18 version of the database. I hadn't copied over the new secrets.json file
before running the server. My previous version of c18 is gone. I'll have to get its data from the website through ssh,
but for now I'll just re-load the data into the proper database. (Note: I had to do a ``python manage.py migrate``
again.)

Updating PgAdmin4
-----------------

There was an update available and I installed it. It now requires a password which seemes to be Dylan Selfie. (Although
that could have been set by me tonight.)

Copying Last-year's Online Database
-----------------------------------

It took some doing, since ``python3.7 manage.py dumpdata gift ... > 2018-database.json`` didn't seem to capture the
Comment model in the gift app. I finally ended up getting into admin to delete all of the data from every model and
then load it all again by doing ``python3.7 dumpdata > 2018-all.json`` through an ssh connection followed by a
``python loaddata 2018-all.json`` on the local computer.

Updating Whatsit
----------------

This was easy to do, just enter each of the five objects and the correct description for each one.

Updating Trivia
---------------

This will be easy once I come up with enough questions for the first set.

Updating Recipe
---------------

This will be hardest, I think, but only in coming up with which recipes to do. I'd also like to add an image of Aunt
Helen to it someplace, and possibly of Mom if I end up using some of her recipes too.

Reinstalling Memories
---------------------

I noticed that no memories were in my c19 database. I will have to copy them from Christmas 2018.









