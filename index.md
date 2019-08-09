## Welcome to Fitness Cheat Sheet

------------------------------------------------------------------------------------------------------------------------------
# !3 FITNESSE KEYWORDS

![:

> **|script   |** This key word must be the first row of every script table

> **|check    |** If the word 'check' is in the first cell of a row, then a function call follows it. The last cell of the table is the expression we expect to be matched by what the function actually returns.

> **|check not|** If the word 'check not' is in the first cell of a row, then a function call follows it. The last cell of the table is the expression we expect not to be matched by what the function actually returns.

> **|ensure   |** If the word 'ensure' is in the first cell, then it should be followed by a function that should return a boolean true for green and false for red.

> **|reject   |** If the word 'reject' is in the first cell, then it should be followed by a function that should return a boolean false for green and true for red.

> **|note     |** If the word 'note' is in the first cell, all other cells in that row will be ignored. Also works if the first cell is blank or begins with # or *.

> **|show     |** If the word 'show' is in the first cell, then it should be followed by a function. A new cell will be added when the test is run, and it will contain the return value of the function.

> **|$VAR=    |** If a symbol assignment is in the first cell, then it should be followed by a function. The symbol is assigned the value returned by that function.

]!

# !3 FITNESSE CONFIGURATION
![:
!define TEST_SYSTEM {slim}: Use the FitNesse SliM test system to run tests
!path ${automated.testing.home}/**.jar: Define classpath for fixtures
]!

# !3 INITIALIZATION
- Initialize !-BaseFixture-! instance that provides access to methods defined in !-BaseFixture.java-!:

`|script|com.appiancorp.ps.automatedtest.fixture.BaseFixture|`

- Initialize !-BaseFixture-! instance that provides access to methods defined in !-TempoFixture.java-!:

`|script|com.appiancorp.ps.automatedtest.fixture.TempoFixture|`

- Initialize !-SitesFixture-! instance that provides access to methods defined in !-SitesFixture.java-!:

`|script|com.appiancorp.ps.automatedtest.fixture.SitesFixture|`

- Initialize Selenium Web Driver and open an instance of the specified browser:

`|setup with|BROWSER_NAME|browser|`

- Configure custom login page fields:

```|setup login with username field|<field ID/Name/Value attribute>|and password field|<field ID/Name/Value attribute>|and login button|<field ID/Name/Value attribute>|```

# !3 NAVIGATION METHODS
Navigate to tempo tab:

|click on menu|TEMPO_MENU_NAME|

Search for a term on News, Reports, or Record List:

|search for|SEARCH_TERM|

# !3 NEWS METHODS
Verify a news post containing specific text is present. The method will wait for the timeout period and refresh up to the configured number of refresh times before failing:

|verify news feed containing text|NEWS_TEXT|is present|

Verify a news post containing specific text is not present:

|verify news feed containing text|NEWS_TEXT|is not present|

Verify a news post containing specific text with a specific label and value is present:

|verify news feed containing text|NEWS_TEXT|and more info with label|LABEL|and value|VALUE|is present|

Verify a news post containing specific text with a specific tag is present:

|verify news feed containing text|NEWS_TEXT|tagged with|TAG_NAME|is present|

Verify a news post with a particular title and comment is present:

|verify news feed containing text|NEWS_TEXT|commented with|COMMENT|is present|

Clicks on the posted link for a news post containing the specific text and verifies that the browser is directed to a URL with the appropriate ID

|verify news feed containing|MESSAGE|link navigation|

Hover over the user profile circle on a news post containing specific text:

|verify hover over news poster circle on post containing|MESSAGE|

Hover over the user profile link on a news post containing specific text:

|verify hover over news poster link on post containing|MESSAGE|

Verify that a news post containing specific text is starred:

|verify post|MESSAGE|is starred|

Click on the record tag on a particular news post:

|click on news feed|NEWS_TEXT|record tag|RECORD_TAG|

Click the user profile circle on a news post containing specific text:

|click user profile circle on post containing|MESSAGE|

Click the user profile link on a news post containing specific text:

|click user profile link on post containing|MESSAGE|

Toggle the 'more info' on a news post containing specific text:

|toggle more info for news feed containing text|NEWS_TEXT|

Delete a news post:

|delete news post|NEWS_TEXT|

Return a string that matches the regex. This could be useful in extracting a system generated value from the news feed:

|get regex|REGEX|group|GROUP|from news feed containing text|NEWS_TEXT|

Return a string that matches the regex from a comment. This could be useful in extracting a system generated value from the news feed:

|get regex|REGEX|group|GROUP|from news feed containing text|NEWS_TEXT|commented with|COMMENT|

Send a news post to a list of participants:

|send post|MESSAGE|to|RECIPIENTS|

Post a kudos message about a user:

|send kudos|MESSAGE|to|RECIPIENT|

Send a locked or unlocked news post to a list of recipients:

|send|LOCKED or UNLOCKED|message|MESSAGE|to|RECIPIENTS|

Add a comment to a news post containing specific text:

|add comment|COMMENT|to post containing|MESSAGE|

Star a news post containing specific text:

|star post containing|MESSAGE|

Filter news feed on supplied filter:

|filter news on|FILTER_NAME|

# !3 TASKS METHODS
Click on the supplied task name:

|click on task|TASK_NAME or TASK_NAME[INDEX]|

Click on task report:

|click on task report|TASK_REPORT_NAME|

Verify if task is present in the user interface. This is useful for determining if security is applied correctly:

|verify task|TASK_NAME or TASK_NAME[INDEX]|is present|

Verify if task is not present in the user interface. This is useful for determining if security is applied correctly:

|verify task|TASK_NAME or TASK_NAME[INDEX]|is not present|

Verify a task with a specific name has a specific deadline (e.g. 1h):

|verify task|TASK_NAME or TASK_NAME[INDEX]|has a deadline of|DEADLINE_TEXT|

Return data, from a task, as a variable using Java Regular Expression:

|get regex|REGEX|group|GROUP|from task name containing text|TASK_TEXT|

Accept a task. This will not return error if task is already accepted:

|accept task|

Send a task from the news message box:

|send task|TASK_MESSAGE|to|RECIPIENT|

Close the social task containing supplied text and add a comment:

|close social task containing|MESSAGE|with comment|COMMENT|

Verify a social task item containing specific text is not present:

|verify task feed containing text|TASK_TEXT|is not present|

# !3 RECORDS METHODS
## !4 RECORD LIST
Click on a record type, use RECORD_NAME[INDEX] to click on the 2nd, 3rd, ... record type with the same label:

|click on record type|RECORD_TYPE_NAME or RECORD_TYPE_NAME[INDEX]|

Populate a user filter with a value:

|populate record type user filter|USER_FILTER_NAME|with|USER_FILTER_VALUE|

Clear a user filter:

|clear record type user filter|USER_FILTER_NAME|

Page through a record grid view. Options include "First", "Previous", "Next", or "Last":

|click on record grid navigation|NAVIGATION_OPTION|

Verify a particular record type user filter is present:

|verify record type user filter|USER_FILTER_NAME|is present|

Verify a record is present:

|verify record|RECORD_NAME or RECORD_NAME[INDEX]|is present|

Verify a record is not present:

|verify record|RECORD_NAME or RECORD_NAME[INDEX]|is not present|

Sort a record grid view by column:

|sort record grid by column|COLUMN_NAME|

## !4 RECORD DASHBOARD
Click on a record. Works for both record list view and record grid view:

|click on record|RECORD_NAME or RECORD_NAME[INDEX] or [INDEX]|

Click on a record view:

|click on record view|VIEW_NAME|

Click on a related action. Works for quick links and on the related action view:

|click on record related action|RELATED_ACTION_NAME|

Verify a record related action is present:

|verify record related action|RELATED_ACTION_NAME|is present|

Verify a record related action is not present:

|verify record related action|RELATED_ACTION_NAME|is not present|

Return data, from a record, as a variable using Java Regular Expression:

|get regex|REGEX|group|GROUP|from record name containing text|RECORD_TEXT|

# !3 REPORTS METHODS
## !4 REPORT LIST
Click on a report:

|click on report|REPORT_NAME or REPORT_NAME[INDEX]|

Verify a report is present:

|verify report|REPORT_NAME or REPORT_NAME[INDEX]|is present|

Verify a report is not present:

|verify report|REPORT_NAME or REPORT_NAME[INDEX]|is not present|

# !3 ACTIONS METHODS
Click on an action. Use index notation to click on the 2nd, 3rd, ... action with the same label:

|click on action|ACTION_NAME or ACTION_NAME[INDEX]|

Verify an action is present:

|verify action|ACTION_NAME or ACTION_NAME[INDEX]|is present|

Verify an action is not present:

|verify action|ACTION_NAME or ACTION_NAME[INDEX]|is not present|

Click on an actions application filter:

|click on application filter|APP_FILTER|

Verify an application is present:

|verify application filter|APPLICATION_NAME|is present|

Verify an application is not present:

|verify application filter|APPLICATION_NAME|is not present|

# !3 INTERFACE METHODS
For populating all types of fields. When populating checkbox, radio, or select fields, [INDICES] can be used.  When populating picker fields the display value must be used:

|populate field|FIELD_LABEL or [INDEX] or FIELD_LABEL[INDEX]|with|VALUE(S)|

Populate a field with a value that contains a comma:

|populate field|FIELD_LABEL or [INDEX] or FIELD_LABEL[INDEX]|with value|VALUE|

Populate the 1st, 2nd, 3rd, ... field of a specific type with no label, currently only compatible with FIELD_TYPE(s) of TEXT, PARAGRAPH, and FILE_UPLOAD. WARNING - Integer, Decimal, and Encrypted text fields will be considered as Text fields:

|populate|FIELD_TYPE|field|[FIELD_INDEX]|with|VALUE(S)|

Populate a field in a section with no label:

|populate field|FIELD_LABEL OR [FIELD_INDEX]|in section|SECTION_NAME|with|VALUE(S)|

Populate a grid field with a value (Column and Row Numbers should be in square brackets []):

|populate grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|column|COLUMN_NAME or [COLUMN_INDEX]|row|[ROW_INDEX]|with|VALUE(S)|

Populate a picker field in a grid cell (Column and Row Numbers should be in square brackets []). This is useful when the picker field suggestions are only a partial match to the input values:

|populate grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|column|COLUMN_NAME or [COLUMN_INDEX]|row|[ROW_INDEX]|with|VALUE(S)|partially matching picker field suggestion|

Populate a grid field with a single value:

|populate grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|column|COLUMN_NAME or [COLUMN_INDEX]|row|[ROW_INDEX]|with value|VALUE|

Clear a field:

|clear field|FIELD_LABEL or [FIELD_INDEX] or FIELD_LABEL[INDEX]|

Remove a specific value from a picker:

|clear field|FIELD_LABEL or [FIELD_INDEX] or FIELD_LABEL[INDEX]|of|VALUE_TO_REMOVE|

Clear a grid field (Column and Row Numbers should be in square brackets []):

|clear grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|column|COLUMN_NAME or [COLUMN_INDEX]|row|[ROW_INDEX]|

Use with FitNesse keyword 'check' to verify form title:

|get form title|

Use with FitNesse keyword 'check' to verify form instructions:

|get form instructions|

Use with FitNesse keyword 'check'  to verify values of field inputs:

|get field|FIELD_LABEL or [FIELD_INDEX] or FIELD_LABEL[INDEX]|value|

Use with FitNesse keyword 'check' to verify values of field inputs in a section:

|get field|FIELD_LABEL or FIELD_LABEL[INDEX]|in section|SECTION_NAME|value|

Return the validation messages from a field. Multiple messages will be concatenated with a comma:

|get field|FIELD_LABEL or [FIELD_INDEX] or FIELD_LABEL[INDEX]|validation message|

Return the link URL:

|get link|LINK_NAME or LINK_NAME[INDEX]|url|

Return the current step of the milestone:

|get milestone|MILESTONE_NAME or MILESTONE_NAME[INDEX] or [MILESTONE_INDEX]|step|

Return the value from a grid cell:

|get grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|column|COLUMN_NAME or [COLUMN_INDEX]|row|[ROW_INDEX]|value|

Return the stored total count:

|get grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|total count|

Return the stored grid current page row count:

|get grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|row count|

Return data, from a from a form title, as a variable using Java Regular Expression:

|get regex|REGEX|group|GROUP|from form title|

Return data, from a form field, as a variable using Java Regular Expression:

|get regex|REGEX|group|GROUP|from field|FIELD_NAME|value|

Return data, from a form field in a section, as a variable using Java Regular Expression:

|get regex|REGEX|group|GROUP|from field|FIELD_NAME|in section|SECTION_NAME|value|

Return data, from a form grid, as a variable using Java Regular Expression:

|get regex|REGEX|group|GROUP|from grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|column|COLUMN_NAME_OR_INDEX|Row|[Row_Number]|value|

Verify field contains value:

|verify field|FIELD_LABEL or [FIELD_INDEX] or FIELD_LABEL[INDEX]|contains|VALUES()|

Verify field value if it contains a comma:

|verify field|FIELD_LABEL or [FIELD_INDEX] or FIELD_LABEL[INDEX]|contains value|VALUE|

Verify field in section contains a value:

|verify field|FIELD_LABEL or [FIELD_INDEX]|in section|SECTION_NAME|contains|VALUE(S)|

Verify field with label is present:

|verify field|FIELD_LABEL or [FIELD_INEDX] or FIELD_LABEL[INDEX]|is present|

Verify field with label is not present:

|verify field|FIELD_LABEL or [FIELD_INEDX] or FIELD_LABEL[INDEX]|is not present|

Verify field with label contains a specific validation message:

|verify field|FIELD_LABEL or [FIELD_INDEX] or FIELD_LABEL[INDEX]|contains validation message|VALIDATION_MESSAGE(S)|

Verify link containing text is present:

|verify link|LINK_TEXT or LINK_TEXT[INDEX]|is present|

Verify link URL contains specific text:

|verify link|LINK_TEXT or LINK_TEXT[INDEX]|URL contains|URL_TEXT|

Verify a milestone is at a particular step:

|verify milestone|MILESTONE_LABEL OR MILESTONE_LABEL[INDEX] or [MILESTONE_INDEX]|step is|STEP|

Verify button with label is present:

|verify button|BUTTON_NAME or BUTTON_NAME[INDEX]|is present|

Verify button with label is not present:

|verify button|BUTTON_NAME or BUTTON_NAME[INDEX]|is not present|

Verify section with label contains a specific validation message:

|verify section|SECTION_NAME|contains validation message|VALIDATION_MESSAGE(S)|

Verify a grid field contains a value (Column and Row Numbers should be in square brackets []):

|verify grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|column|COLUMN_NAME or [COLUMN_INDEX]|row|[ROW_INDEX]|contains|VALUE(S)|

Verify a grid field contains a single value:

|verify grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|column|COLUMN_NAME or [COLUMN_INDEX]|row|[ROW_INDEX]|contains value|VALUE|

Verify if row in grid is selected (Row Numbers should be in square brackets []):

|verify grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|row|[ROW_INDEX]|is selected|

Verify a chart with given label is present:

|verify chart|CHART_LABEL|is present|

Verify a chart with given label is not present:

|verify chart|CHART_LABEL|is not present|

Verify a video with given source is present. You can provide a substring of the source:

|verify video|VIDEO_SOURCE or VIDEO_SOURCE[INDEX]|is present|

Verify a video with given label is not present. You can provide a substring of the source:

|verify video|VIDEO_SOURCE or VIDEO_SOURCE[INDEX]|is not present|

Verify a web content with given source is present. You can provide a substring of the source:

|verify web content|WEB_CONTENT_SOURCE or WEB_CONTENT_SOURCE[INDEX]|is present|

Verify a web content with given source is not present. You can provide a substring of the source:

|verify web content|WEB_CONTENT_SOURCE or WEB_CONTENT_SOURCE[INDEX]|is not present|

Click on the save changes link:

|click on save changes|

Click on button:

|click on button|BUTTON_NAME or BUTTON_NAME[INDEX]|

Click on a link:

|click on link|LINK_NAME or LINK_NAME[INDEX]|

Click on a milestone step:

|click on milestone|MILESTONE_NAME or MILESTONE_NAME[INDEX] or [MILESTONE_INDEX]|step|STEP|

Select a radio option:

|click on radio option|RADIO_OPTION or RADIO_OPTION[INDEX]|

Check a checkbox option with the given choice label:

|click on checkbox option|CHECKBOX_OPTION or CHECKBOX_OPTION[INDEX]|

Click on an image or text link in a grid cell. Useful for clicking the "delete row" X cell to delete a row:

|click on grid|GRID_NAME or GRID_NAME[INDEX] or [GRID_INDEX]|column|COLUMN_NAME or [COLUMN_INDEX]|row|[ROW_INDEX]|

Click on the add row link for a grid:

|click on grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|add row link|

Navigate through pages of a grid. Valid navigations are "first", previous, next, or "last":

|click on grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|navigation|NAV_REFERENCE|

Click on a card:

|click on card|CARD_LINK_NAME or CARD_LINK_NAME[INDEX]|

Toggle visibility of section:

|toggle section|SECTION_NAME|visibility|

Toggle visibility of box:

|toggle box|BOX_NAME  or [BOX_INDEX] or BOX_NAME[INDEX]|visibility|

Select row in grid (Row Numbers should be in square brackets []):

|select grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|row|[ROW_INDEX]|

Select all rows in a grid.  Can also be used to de-select all rows:

|select all rows in grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|

Sort grid by column name:

|sort grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|by column|COLUMN_NAME|

Return count of rows in an editable or paging grid:

|count grid|GRID_NAME or [GRID_INDEX] or GRID_NAME[INDEX]|rows|

Store in the defined variable the index of the grid that matches that list of header labels separated by ";". The list of headers can be a subset but must start from the left. The wildcard "*" can be used if a header doesn't have a label. In the gridField the selectable column counts as the first column. The method will return a value if only one grid is matched:

|$<variable>=|get Grid Index|* ; Header 2|

# !3 SITES METHODS
Navigate to an Appian Site:

|navigate to site|SITE_URL|

Navigate to specific page on an Appian Site:

|navigate to site|SITE_URL|page|PAGE_URL|

Click on an Appian Site page from within a site. Although pages are capitalized on the site, the SITE_NAME must match what is entered when creating the page:

|click on site page|SITE_PAGE|

Open settings menu from a site:

|open settings menu|

Navigate to the user profile from the sites menu:

|open user profile|

Navigate to another site from Sites Discoverability menu:

|use discoverability to navigate to|SITE_NAME|

# !3 UTILITY METHODS
Initialize Selenium Web Driver and open browser. Options include FIREFOX, CHROME:

|setup with|BROWSER_NAME|browser|

Tear down Selenium Web Driver and close browser:

|tear down|

Call a web API and return result as a string. User defined by username must have permission to access the web API:

|get web api|WEB_API_ENDPOINT|with username|USERNAME|

Call a web API and return result as a string. User defined by role must have permission to access the web API:

|get web api|WEB_API_ENDPOINT|with role|ROLE_NAME|

Call a web API with a body and return result as a string. User defined by username must have permission to access the web API:

|post web api|WEB_API_ENDPOINT|with body|BODY|with username|USERNAME|

Call a web API with a body and return result as a string. User defined by role must have permission to access the web API:

|post web api|WEB_API_ENDPOINT|with body|BODY|with role|ROLE_NAME|

Set the default Appian URL:

|set appian url to|APPIAN_URL|

Set the default Appian version:

|set appian version to|APPIAN_VERSION|

Set the Appian locale used for date and datetime formatting, options include en_US or en_GB (defaults to en_US):

|set appian locale to|APPIAN_LOCALE|

Used as relative datetime for date/time fields:

|set start datetime|

Used as the wait timeout in between each command:

|set timeout seconds to|TIMEOUT_SECONDS|

Set the folder where screenshots will be saved. This will create new folders if necessary. Terminate path with "/" to ensure folder creation (Defaults to ${automated.testing.home}/screenshots/):

|set screenshot path to|SCREENSHOT_PATH|

Take screenshots for every failed test case if provided value is true (Default true):

|set take error screenshots to|SCREENSHOT_BOOLEAN|

Stop FitNesse test on any error if provided value is true (Default false):

|set stop on error to|STOP_ON_ERROR_BOOLEAN|

Set a test variable with a value that is a JSON string. The variable can then be accessed by using tv!VARIABLE_NAME.JSON_PATH:

|set test variable|VARIABLE_NAME|with|JSON_VALUE|

Take a screenshot and name the file (do not include the extension):

|take screenshot|FILE_NAME|

Login to the previously set Appian URL with a username and the associated password for the user provided in the configs/user.properties file:

|login with username|USERNAME|

Login to the previously set Appian URL with a username/password that has an associated role provided in the configs/user.properties file:

|login with role|USER_ROLE|

Login to the previously set Appian URL with the given username and password

|login with username|USERNAME|and password|PASSWORD|

Login to the previously set Appian URL, containing terms and conditions, with the given username and password:

|login with terms with username|USERNAME|and password|PASSWORD|

Login to the previously set Appian URL, containing terms and conditions, with the given username and the associated password provided in the configs/user.properties file:

|login with terms with username|USERNAME|

Login to the previously set Appian URL containing terms and conditions, with a username/password that has an associated role provided in the configs/user.properties file:

|login with terms with role|USER_ROLE|

Wait for relative amount of time (e.g. +1 days, +1 hours):

|wait for|RELATIVE_PERIOD|

Wait until relative time (e.g. 2018-01-11 12:31):

|wait until|RELATIVE_PERIOD|

Use with $VARIABLE_NAME= to generate random strings of a specific length:

|get random string|STRING_LENGTH|

Use with $VARIABLE_NAME= to generate random alphabetical string of a specific length:

|get random alphabet string|STRING_LENGTH|

Use with $VARIABLE_NAME= to generate random integer in a specific range:

|get random integer from|MIN_INT|to|MAX_INT|

Use with $VARIABLE_NAME= to generate random decimal in a specific range:

|get random decimal from|MIN_DECIMAL|to|MAX_DECIMAL|

Use with $VARIABLE_NAME= to generate random decimal in a specific range up to a specific decimal places:

|get random decimal from|MIN_DECIMAL|to|MAX_DECIMAL|with|DECIMAL_PLACES|

Use with $VARIABLE_NAME = to assign a tv! variable to a local variable:

|get test variable|tv!VARIABLE_NAME.JSON_PATH|

Resize the browser window:

|resize window width|WIDTH|height|HEIGHT|

Open a particular URL, useful for logging in if using SSO:

|open|URL|

Refresh screen:

|refresh|

Logout of Appian site:

|logout|

Verify if text is present anywhere in the user interface:

|verify text|TEXT_ON_INTERFACE|is present|

--------------------------------------------------------------------------------------------------------------------------


You can use the [editor on GitHub](https://github.com/ViniciusMRocha/fitness-cheat-sheet/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/ViniciusMRocha/fitness-cheat-sheet/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
