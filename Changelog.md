## Robotium Changelog ##

## Robotium 5.4.1 ##

This version of Robotium comes with several cool new features like illustrate, clickInRecyclerView and commandLogging. We’ve also updated the Activity handling and the various click methods.

**New Functionality:**

  * illustrate(Illustration illustration) - Draws an arbitrary path with an arbitrary amount of points on the screen
  * clickInRecyclerView(int itemIndex) - Clicks a specified item index in the first RecyclerView it finds
  * clickInRecyclerView(int itemIndex, int recyclerViewIndex) - Clicks a specified item index in the RecyclerView matching the specified recyclerViewIndex
  * clickLongInRecycleView(int itemIndex) - Long clicks a specified item index in the first RecyclerView it finds
  * clickLongInRecycleView(int itemIndex, int recyclerViewIndex) - Long clicks a specified item index in the RecyclerView matching the specified recyclerViewIndex
  * clickLongInRecycleView(int itemIndex, int recyclerViewIndex, int time) -  Long clicks the specified itemIndex in the RecyclerView matching the specified recyclerViewIndex for the specified amount of time.

New settings Solo.Config:

  * public String webFrame - Set the web frame to be used by Robotium. Default value is "document"
  * public boolean commandLogging - Set to true if command logging should be enabled. Default value is false
  * public boolean commandLoggingTag - Set the commandLogging tag. Default value is "Robotium"

Bugs/Enhancements fixed:

  * Issue-309 - command logging
  * Issue-647 - need method to switch to iframe context
  * Issue-661 - xpath result contains only one node
  * Issue-673 - stop ActivityMonitor when calling finishOpenedActivities

## Robotium 5.3.1 ##

We’ve focused on improving various parts of Robotium. For example the click logic and speed has been improved. We’ve introduced new features like setWiFiData() and fixed bugs in various areas.

**New Functionality:**

  * setWiFiData - Set if WiFi data should be turned on or off.
  * setMobileData - Set if mobile data should be turned on or off.
  * getView(Object tag) - Get a View with a specified tag.
  * getView(Object tag, int index) - Get a View with a specified tag and index.
  * waitForView(Object tag) - Wait for a View with a specified tag.
  * waitForView(Object tag, int minimumNumberOfMatches, int timeout, boolean scroll) - Wait for a View with a specified tag. Set minimum number of matches and if scrolling should be performed.
  * The scroll methods now support RecyclerViews.
  * In Solo.Config trackActivities can be set to false to turn off Activity handling.

## Robotium 5.2.1 ##

We’ve focused on improving the various scroll methods, both by speeding them up and also by improving the logic. We’ve introduced new features like unlockScreen() and fixed bugs in various areas.

**New Functionality:**

  * unlockScreen() - Unlocks the screen lock.
  * getCurrentViews(Class classToFilterBy, boolean includeSubclasses) - New parameter includeSubclasses set to true if also subclasses should be returned.
  * scrollToSide(Side side, float scrollPosition, int stepCount) - Parameter stepCount for users to decide the speed of the scroll.
  * scrollViewToSide(View view, Side side, float scrollPosition, int stepCount) - Parameter stepCount for users to decide the speed of the scroll.


## Robotium 5.1 ##

Our work on improving Robotium has continued and we now have the fastest, most accurate and stable version of Robotium yet.

Note: package name is now: com.robotium.solo.

**New Functionality:**

  * Solo(Instrumentation instrumentation, Config config, Activity activity) - New constructor.
  * pressSoftKeyboardSearchButton() - Presses the search button on the soft keyboard.
  * getWebElements() - Returns all the WebElements displayed in the active WebView.
  * getWebElements(By by) - Returns all the WebElements displayed in the active WebView matching the specified By object.
  * setNavigationDrawer(int status) - Sets the status of the NavigationDrawer.
  * getConfig() - Returns the Config used by Robotium.

## Robotium 5.0.1 ##

A new SoloConfig class is Included in this release, where Robotium Developers can change various things like default timeouts, screenshot location, screenshot type, scrolling, and web element click behaviour. Also several improvements to the internal classes.

Note: package name has been changed to: com.robotium.solo.


**New Functionality:**

  * pressSoftKeyboardNextButton()
  * waitForEmptyActivityStack()

New class Solo.Config:

  * int timeout\_large - The timeout length of the waitFor methods.
  * int timeout\_small - The timeout length of the get, is, set, assert, enter and click methods.
  * String screenshotSavePath - The screenshot save path.
  * ScreenshotFileType screenshotFileType - The screenshot file type, JPEG or PNG.
  * boolean shouldScroll - Set to true if the get, is, set, enter, type and click methods should scroll.
  * boolean useJavaScriptToClickWebElements  - Set to true if JavaScript should be used to click WebElements.


**Improvements to:**

  * All the click methods. Improved behaviour in unfavourable situations.
  * The waitForDialogToOpen & waitForDialogToClose methods.
  * The internal View handling.
  * TakeScreenshot() now supports GLSurfaceViews with OpenGL ES 3.0.

## Robotium 4.3.1 ##

Purely a maintenance release where bugs have been fixed and support for Android API level 19 is added

**API level 19**

  * Full support for Android API level 19

**Issues fixed:**

  * Issue-549 In RobotiumUtils.java , Matcher.find() maybe invoked
  * issue-543 Button with "\n" in text can't be found
  * Issue-538 NullPointerException in ScreenshotTaker.getBitmapOfView
  * Issue-527 Solo.pinchToZoom does not work properly

**Improvements to:**

  * getView(String id, int index) Works better with Android id's
  * waitForDialogToOpen() Fixed timing issue
  * clickOnActionbarHomeButton() Fixed thread access warning
  * waitForView(View view) Improved recognition of Views

## Robotium 4.3 ##

The main goal of this release has been to go over the existing code and improve it. Besides bug fixes and improvements, new features have also been introduced.


**New Functionality:**

  * waitForDialogToOpen()
  * waitForDialogToClose()
  * getString(String id)
  * scrollToSide(int side, float scrollPosition)
  * scrollViewToSide(View view, int side, float scrollPosition)
  * WebElement.setAttributes(Hashtable<String,String> attributes)
  * WebElement.getAttribute(String attributeName)


**Improvements to:**

  * getView(String id) Also works with android.R.id's
  * hideSoftKeyboard() Always closes the soft keyboard
  * clickOnMenuItem() Improved waiting
  * enterText(), clearEditText() Faster then before
  * drag() closes the soft keyboard
  * takeScreenshot() better GL support
  * searchText/waitForText support for line breaks
  * By.id returns dynamic id's
  * getCurrentWebElements() better css and xpath support


## Robotium 4.2 ##
This version comes with some really cool new features like pinchToZoom and startScreenshotSequence. Besides new functionality a lot of effort has gone into updating existing methods to make them more stable. Also the web functionality has been re-written in order to have full support for existing web frameworks.

**New Functionality:**

  * getView(String id)
  * getView(String id, int index)
  * pinchToZoom(PointF startPoint1, PointF startPoint2, PointF endPoint1, PointF endPoint2)
  * rotateLarge(PointF center1, PointF center2)
  * rotateSmall(PointF center1, PointF center2)
  * swipe(PointF startPoint1, PointF startPoint2, PointF endPoint1, PointF endPoint2)
  * clickOnScreen(float x, float y, int numberOfClicks)
  * clearLog()
  * waitForView(int id)
  * waitForView(int id, int minimumNumberOfMatches, int timeout)
  * waitForView(int id, int minimumNumberOfMatches, int timeout, boolean scroll)
  * startScreenshotSequence(String name)
  * startScreenshotSequence(String name, int quality, int frameDelay, int maxFrames)
  * stopScreenshotSequence()


**New class Timeout:**

  * getLargeTimeout()
  * setLargeTimeout(int milliseconds)
  * getSmallTimeout()
  * setSmallTimeout(int milliseconds)

## Robotium 4.1 ##
A lot of work has gone into fixing issues and improving the overall experience making this the best version of Robotium yet!.

**New Functionality:**

  * waitForActivity(Class<? extends Activity> activityClass)
  * waitForActivity(Class<? extends Activity> activityClass, int timeout)
  * getWebUrl()
  * hideSoftKeyboard()
  * getView(int id, int index)
  * takeScreenshot() also works with GLSurfaceViews

## Robotium 4.0 ##
Robotium now supports hybrid apps. Web support has been built in, searchText(), waitForText(), clickOnText(),  scroll() methods, takeScreenShot() etc, now support WebViews.

**New Functionality:**

  * waitForCondition(Condition condition, final int timeout)
  * waitForWebElement(By by) //Example: waitForWebElement(By.id("id"));
  * waitForWebElement(By by, int timeout, boolean scroll)
  * waitForWebElement(By by, int match, int timeout, boolean scroll)
  * clickOnWebElement(WebElement webElement)
  * clickOnWebElement(By by)
  * clickOnWebElement(By by, int match)
  * clickOnWebElement(By by, int match, boolean scroll)
  * enterTextInWebElement(By by, String text)
  * typeTextInWebElement(By by, String text)
  * typeTextInWebElement(By by, String text, int match)
  * typeTextInWebElement(WebElement webElement, String text)
  * clearTextInWebElement(By by)
  * getWebElement(By by, int index)
  * getCurrentViews(Class classToFilterBy)
  * getCurrentViews(Class classToFilterBy, View parent)
  * takeScreenshot(String name, int quality)

**New class RobotiumUtils:**

  * removeInvisibleViews(Iterable viewList)
  * filterViews(Class classToFilterBy, Iterable<?> viewList)
  * filterViewsToSet(Class classSet[.md](.md), Iterable viewList)
  * sortViewsByLocationOnScreen(List  views)
  * sortViewsByLocationOnScreen(List views, boolean yAxisFirst)
  * getNumberOfMatches(String regex, View view, Set uniqueTextViews)

**Methods removed:**
  * getAllOpenedActivities()
  * finishInactiveActivities()
  * getCurrentXViews //replaced by getCurrentViews(Class classToFilterBy). Example: getCurrentViews(ListView.class)

## Robotium 3.6 ##
Full support for Android 4.2 (API Level 17). A part from several bug fixes, more optimisations and improvements have been done which results in the fastest and best Robotium to date.

**New Functionality:**
  * scrollViewToSide(View view)
  * scrollListToLine(int index, int line)
  * scrollListToLine(AbsListView listView, int line)

## Robotium 3.5.1 ##
New functionality, bug fixes and more improvements to the activity handling. The memory footprint has been further reduced  making this version of Robotium even lighter then before..

**New Functionality:**
  * clickOnView(View view, boolean immediately)
  * scrollDownList(AbsListView list)
  * scrollUpList(AbsListView list)
  * scrollListToBottom(AbsListView list)
  * scrollListToTop(AbsListView list)
  * getCurrentNumberPickers()


## Robotium 3.4.1 ##
New functionality, bug fixes, as well as important changes to the activity handling. The memory footprint is reduced significantly and big test projects which had memory issues before run well now.

**New Functionality:**
  * scrollToTop()
  * scrollToBottom()
  * scrollListToTop(int index)
  * scrollListToBottom(int index)
  * waitForFragmentById(int id)
  * waitForFragmentByTag(String tag)
  * waitForLogMessage(String logMessage)
  * clickOnActionBarHomeButton()
  * takeScreenShot(String filename)


## Robotium 3.3 ##
Besides implementing new features and fixing bugs, areas which have previously been problematic have now been modified. The first area is the scroll functionality that has been modified in order to better decide which object that should be scrolled. The second area is the Activity manager.  The garbage collector can now garbage collect an Activity and all its objects without Robotium blocking it. This leads to a much smaller memory footprint.

**New Functionality:**
  * getCurrentImageViews(View parent)
  * takeScreenshot()
  * clickOnActionBarItem(int resourceId)

## Robotium 3.2.1 ##
Many bugs have been fixed and new functionality has been implemented.

**New Functionality:**
  * typeText(int index, String text)
  * typeText(`EditText` editText, String text)
  * finishInactiveActivities()

**Issues Fixed:**
  * getCurrentActivity() not returning the correct Activity when back key is used (on Android 3.0+)


## Robotium 3.1 ##
Most efforts have gone into improvements and also fixing issues that were
introduced in the 3.0 release. Also, many improvements have been made
in the activity methods. If you have had issues with
finishOpenedActivities() then please try this version instead.

**New Functionality:**
  * getView(Class viewClass, int index)   //Returns a view with a given class and index

## Robotium 3.0 ##
This release is
the fastest, lightest and most stable version of Robotium yet. More or
less all the code has been modified and improved in one way or
another, leading to a very stable version.

One big change which breaks backward compatibility is that activities
are now closed with the new method finishOpenedActivities().
Finalize() does not close activities any more. If you have used
finalize() before, you will need to change that to
finishOpenedActivities() instead.

**New Functionality:**
  * finishOpenedActivities()  //Closes the opened activities (replaces inalize())
  * waitForText(String text, int minimumNumberOfMatches, long timeout, boolean scroll, boolean onlyVisible)
  * waitForView(View view)
  * waitForView(View view, int timeout, boolean scroll)

**Modified methods:**
  * finalize() does not close activies anymore!
  * searchText() also searches error messages.

## Robotium 2.5 ##
Robotium now supports
Android 3.2, Honecomb. Some minor annoying issues have also been fixed
to improve the overall experience.

**New Functionality:**
  * getText(String text, boolean onlyVisible)
  * getButton(String text, boolean onlyVisible)
  * getEditText(String text, boolean onlyVisible)

## Robotium 2.4 ##
Most of the work in this release has
gone into correcting defects and improving Robotium. The assert
methods have been re-designed in order to improve stability.

**New Functionality:**
  * waitForActivity(String name) which includes a default timeout of 20 seconds (similar to the other waitFor methods).

## Robotium 2.3 ##
It is mainly a maintenance release where
the issues reported have been corrected.

**New Functionality:**
  * getActivityMonitor() which returns the activity monitor used by Robotium. Some users have requested the possibility to disable it in order to set up their own activity monitors

## Robotium 2.2 ##
The biggest news in this release is a
new constructor which allows for only the instrumentation object to be
given: Solo(Instrumentation instrumentation). The Activity can later
be started and Robotium will then pick it up. This will solve some
problems that have been experienced when a swift splash screen has
been failed to be recognized by Robotium as it happened before it was
set up. Now the activity can be started after Robotium.

Also the whole view fecthing mechanism has been modified and improved
so that issues experienced with dialogs are solved. Changes has also
been made to improve performance and memory footprint.

**New Functionality:**
  * Solo(Instrumentation instrumentation)
  * clickLongInList(int line)
  * clickLongInList(int line, int index)
  * clickLongInList(int line, int index, int time)
  * setSlidingDrawer(int index, int status)
  * setSlidingDrawer(`SlidingDrawer` slidingDrawer, int status)

## Robotium 2.1 ##
This release
not only brings new features but also a lot of internal changes and
improvements. Most of the work in this release has gone into making
Robotium better then before. The memory footprint has been reduced
which results in a more effective and lighter version of Robotium.
Furthermore the improvements that have been made to the whole scroll
and view fetching functionality makes this the smartest Robotium to
date.

**New Functionality:**
  * waitForView(Class`<T>` viewClass)
  * getCurrentViews()
  * pressMenuItem(int index, int itemsPerRow)
  * sendKey() supports any key event
  * clickInList() has been completely re-designed to support all list implementations.
  * Scrolling of scrollViews has also been completely re-designed to increase speed and accuracy

## Robotium 2.0.1 ##
The 2.0 issues have been solved and
now it should work really well. It has been optimized and improved and
it is definitely faster then previous releases. It also supports more
(complex) applications. A lot of methods have been rewritten for this
release.

**New Functionality:**
  * setDatePicker(index, year, monthOfYear, dayOfMonth)
  * setTimePicker(index, hour, minute)
  * clickLongOnView(view, time)
  * clickLongOnText(String text, int match, int time)
  * setProgressBar(index, progress)
  * Full support for `ExpandableListViews`

## Robotium 2.0 ##
In this release two major problems have been resolved. The first problem was that in some application all views were not found. The second problem was that finalize() sometimes did not successfully close down Applications when used in a tearDown. To solve these problems some parts of Robotium have been fully rewritten and
improved.  Besides resolving these issues, optimizations and bugfixes
have also been made.

**New Functionality:**
  * setDatePicker(index, year, monthOfYear, dayOfMonth)
  * setTimePicker(index, hour, minute)
  * clickLongOnView(view, time)
  * clickLongOnText(String text, int match, int time)
  * setProgressBar(index, progress)
  * Full support for `ExpandableListViews`

## Robotium 1.9.0 ##
This is a release where most of the
work has gone into stability issues. After increasing so much in
functionality ever since the first release, this work was needed in
order to make the existing functionality perform well. Quality wise I
am very happy with this release. A new method waitForView() has been
implemented which more or less all the methods now use before trying
to do something. The scrolling of lists has been completely re-done
and now the scroll is not only very fast but also controlled and
precise.

**New Functionality:**
  * waitForView(final Class`<T>` viewClass, final int minimumNumberOfMatches, final int timeout) Waits for a view a certain amount of time and returns true or false depending on result.
  * enterText(`EditText` editText) enters text into an `EditText`
  * clearEditText(`EditText` ediText) clears an `EditText`
  * isTextChecked(String text) checks if a `CheckedTextView` or `CompoundButton` is checked

**Re-written functionality:**
  * `ScrollList`() that is now twice as fast as before and exactly one page is scrolled at a time.
  * Multiple changes have also been made into various methods in order to not only improve functionality but also performance and stability

## Robotium 1.8.0 ##
It brings new functionality as well as
many bug fixes and improvements in the existing code.

**New Functionality:**
  * getButton(String text), getText(String text) and getEditText(String text) which will return the view that displays a certain text so that questions can be asked directly to the view object it self
  * getView(int id) has also been added which will return a view depending on its id
  * searchText(String text, boolean onlyVisible), searchButton(String text, boolean onlyVisible) which will only search for visible views on the screen
  * isToggleButtonChecked(String text) and isToggleButtonChecked(int index) will check if a `ToggleButton` is checked
  * isSpinnerTextSelected(int index, String text) and isSpinnerTextSelected(String text) will check if a spinner text is selected
  * sendKey(Solo.CALL) and sendKey(Solo.ENDCALL) has been added to the existing keys

**Re-written functionality:**
  * enterText() that works in a whole new way now and will work much better and faster then the last solution for entering text
  * scrollDown() and scrollUp() have been optimized and also now check for and locate a draggable area before trying to scroll

## Robotium 1.7.1 ##
Fix to a problem where sometimes
Robotium would not return to the shown activity after a dialog was
shown. That problem is now fixed and probably it fixes a
lot of other issues that people have experienced. Besides that, some
other small bugfixes have been made.

## Robotium 1.7.0 ##
In this release a great deal of time and effort went into improving
the existing functionality.

**New Functionality:**
  * clickLongOnScreen()
  * clickOnText(String text, int matches, boolean scroll)
  * getImage()
  * getString()
  * goBackToActivity()
  * clickOnMenuItem(String text, boolean subMenu)
  * waitForActivity() and more.

## Robotium 1.6.0 ##
A lot of improvements have been done to the previous methods especially the click, search and scroll methods. Also a lot more logging is done and more precise Assert messages are shown.

**New Functionality:**
  * assertLowMemory()
  * clickOnImageButton()
  * clickOnCheckBox()
  * isCheckBoxChecked()
  * getCurrentCheckBoxes()
  * getCurrentImageButtons()
  * waitForText(String text, int matches, long timeout, boolean scroll)
  * searchText(Stringsearch,intmatches,booleanscroll)
  * clickOnEditText()
  * clickOnText(Stringtext, int match)
  * clickLongOnText(String text, int match)

## Robotium 1.5.0 ##
This release includes full support for Dialogs, Toasts, Menus and
Context Menus for all the methods in Robotium!

**New Functionality:**
  * waitForText()
  * clearEditText()
  * clickOnMenu()
  * sendKeys()
  * isRadioButtonChecked()
  * waitForDialogToClose()

## Robotium 1.4.0 ##
A lot of work has gone into optimizing and improving the existing
functionality. More or less all the methods have been modified and
improved. Robotium is now well prepared for a wide variety of Android
applications.
There is no need to add the GET\_TASKS permission tag into the application that will be tested! No modification at all of the application that will be tested is needed.

**New Functionality:**
  * setActivityOrientation()
  * clickInList()
  * clickOnToggleButton()

## Robotium 1.3.1 ##
A lot of work has gone into making it even faster then before. It is
also more robust now as more checks are done before Robotium tries to
do something. This results in a more stable and secure execution.

**New Functionality:**
  * getAllOpenedActivities()
  * scrollDownList()
  * clickLongOnScreen()
  * clickLongOnTextAndPress()

## Robotium 1.2.1 ##
A lot of work has been done to improve the architecture for faster execution. Robotium-Solo is now blazingly fast. Also most of the previous methods have been rewrittenin order to improve speed, decision makings and stability.

**New Functionality:**
  * assertCurrentActivity()
  * pressSpinnerItem()
  * getCurrentListViews()

## Robotium 1.1.1 ##
Changes include clicking on menu items, clicking on back hard key, much more
advanced enterText() that works in all text fields. Also general
optimizations of the code has been performed for a stable and fast
execution.

**New Functionality:**
  * clickOnMenuItem(String text)
  * goBack()
  * enterText(int index, String text)