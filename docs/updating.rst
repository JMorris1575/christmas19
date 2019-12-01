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

