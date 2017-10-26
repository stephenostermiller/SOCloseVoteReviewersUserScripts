# User Scripts

This repository contains various [Tampermonkey](http://tampermonkey.net/) (Chrome, Opera Next, Safari, Firefox) / [Greasemonkey](http://www.greasespot.net/) (Firefox) user scripts that add features to Stack Exchange web interfaces, such as the review queues, the chat room, and the Markdown editor.

Jump to:
- [SO Close Vote Request Generator](#so-close-vote-request-generator)
  - [SO Close Vote Request Generator (bookmarklet)](#so-close-vote-request-generator-bookmarklet)
- [Magic™ Editor](#magic-editor)

## SO Close Vote Request Generator
This script sends a `[tag:cv-pls]` message to the site's chatroom for the post you are currently viewing. It should work on any Stack Exchange site, if it doesn't then please submit an issue.

### Use Case
Close Vote requests should be used when a question meets any of the following criteria:

* Is in a low traffic tag, so unlikely to be closed naturally
* Should be closed quickly, to avoid FGITW
* Is old but attracting attention from new users

Otherwise, you should wait to see if it gets closed naturally. If the question doesn't get closed within a reasonable amount of time, then you can consider sending a close vote request. In general, large amounts of close vote requests from a single user in a short span of time is considered spam.

Sending a close vote request does not obligate any user to contribute a close vote, it is a request for others to review your close vote decision. Any user contributing their own close votes to questions you've requested a vote review for is doing so of their own prerogative. If a user thinks that you've supplied an incorrect reason or that the question is on-topic or can be easily edit into shape, they should tell you why. This does not mean that person is inherently any more correct than you are, it is an opinion.

**Please use the reason that you voted or flagged!** You are submitting a request for review of *your* close vote decision. Users will reply to your review request based on the reason that you enter. If you don't have 3000 reputation yet (and don't have close votes) you should be submitting requests for the close reason that *you* flagged it to be closed for. This is an educational tool for all of us to learn exactly what is on-topic and what is off-topic.

### Installation
To install this script [click here](https://rawgit.com/SO-Close-Vote-Reviewers/UserScripts/master/SECloseVoteRequestGenerator.user.js) or otherwise visit the following URL, and Greasemonkey/Tampermonkey should ask you to install it.

     https://rawgit.com/SO-Close-Vote-Reviewers/UserScripts/master/SECloseVoteRequestGenerator.user.js
     
### Updating
This script has an auto-update feature. It will check for a new version every time the script is run, don't worry it is a very lightweight request. If there is an update available, the script will ask you if you want to install it automatically or not. If not, it will not remind you for that version.

To update manually you can visit the above URL again, or select <kbd>Check for updates</kbd> from the <kbd>cv-pls</kbd> menu.

### Issues & enhancement requests
Before raising new issues, please review the [currently known issue list](https://github.com/SO-Close-Vote-Reviewers/UserScripts/issues?q=is%3Aissue+is%3Aopen+label%3Ascript%3ASOCloseVoteRequestGenerator).

<!-- I used http://meyerweb.com/eric/tools/dencoder/ to encode the issue report template -->
To report a new issue or request an enhancement, create a GitHub Issue Report using [this template](https://github.com/SO-Close-Vote-Reviewers/UserScripts/issues/new?labels=script%3ASOCloseVoteRequestGenerator&body=**Script%3A**%20Close%20Vote%20Request%20Generator%0A**Issue%20type%3A**%20Bug%20%2F%20Enhancement%20%2F%20Question%20(pick%20one)%0A**Link%20to%20example%20post%3A**%20(where%20can%20the%20problem%20be%20reliably%20replicated%3F)%0A%0AProblem%20description...) (requires a GitHub account).

As an alternative, you may send a Pull request for your own fixes or enhancements.

### Target Chat Room
The default chat room is [SO Close Vote Reviewers](http://chat.stackoverflow.com/rooms/41570/so-close-vote-reviewers).

The room URL that you enter into the input field *must* be a valid chatroom URL. The script *will* yell at you if it is not. 

When the room selection menu is closed, the link will have the name of the current room. When the room selection menu is open, the link will say "Set target room:". Clicking on the link will open and close the room selection menu.

Copy the chatroom URL from your address bar and paste it into the input field below the room list. Clicking <kbd>Set</kbd> adds the room to the room list and sets it as the default room for that site. Per-site metas and Stack Exchange sub domains each have their own settings.

### Sending Requests
Requests generated by this script will be in the following format and can be sent whether you are in the target room or not, as long as you have write access. 

    [tag:cv-pls] reason [title](url) - [user](url) time

1. Select <kbd>Send request</kbd> from the <kbd>cv-pls</kbd> menu.
  *  Or press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>A</kbd>
2. Enter your reason into the input provided.
  *  Any markdown that is acceptable in chat is acceptable in the reason dialog.
3. Click <kbd>Send</kbd> or press <kbd>Enter</kbd> to submit the request. 

A notification will pop-up if the request was sent successfully.

### Short Reasons
This script has a short reason replacement feature. The script will split the reason that you entered by space characters, any piece of the string that is an exact match for any of the following letters will be replaced with its corresponding long reason.

* `t: too broad` 
* `u: unclear`
* `p: pob`
* `d: duplicate`
* `m: no mcve`
* `r: no repro`
* `s: superuser`
* `f: serverfault`
* `l: library/tool/resource`

### SO Close Vote Request Generator (bookmarklet)
In some environments it's not possible to install user scripts. In order to facilitate making `cv-pls` requests in such situations, there's a version of the SO Close Vote Request Generator as a [bookmarklet](https://www.google.com/search?q=bookmarklet).

#### Using the bookmarklet:
You will be prompted to enter a reason for the request. After entering the reason, the text for the formatted `cv-pls` will be copied to the clipboard.  If the bookmarklet was unable to copy the text to the clipboard, a notification will be displayed at the top of the page from which you can copy the text.

#### Creating the bookmarklet:
In most browsers, but not Edge, you can add a bookmarklet by creating a bookmark/favorite and changing the URL/location to the minified version of the bookmarklet below.  The bookmarklet is minified in order to fit in the 2088 character limit imposed by some browsers (e.g. IE, Edge). The [minified version](SECloseVoteRequestGenerator-bookmarklet.min.js) of the bookmarklet is:

    javascript:void(function(){function t(){try{history.replaceState({},'',a)}catch(t){}}var e,o={t:'Too Broad',u:'Unclear',p:'Primarily Opinion Based',o:'Opinion Based',d:'Duplicate',m:'No MCVE',r:'Typo or Cannot Reproduce',g:'General Computing',s:'Super User',f:'Server Fault',l:'Request for Off-Site Resource',get:function(t){var e=t.split(' ');return e.forEach(function(t,r){e[r]=o.hasOwnProperty(t)&&'get'!==t?o[t]:t}),e.join(' ')}},r=window,n=r.location,a=n.href,s=$(r),i=s.scrollTop(),l=StackExchange.notify,c=($('.special-status .question-status H2 B').filter(function(){return/hold|closed|marked/i.test($(this).text())}).length?'reopen':'cv')+'-pls',u='https://'+n.hostname,p=window.prompt('Request reason:','');if(p){p=o.get(p);var h,g='['+$('#question-header h1 a').text().replace(/(\[|\])/g,'\\$1').replace(/^\s+|\s+$/gm,'')+'‭]('+u+$('#question .short-link').attr('href')+')',d=$('.post-signature:not([align=\'right\'],#popup-close-question .post-signature) .user-details').text().trim().match(/[^\n]+/)[0].trim(),f=$('#question a.post-tag').first().text(),m=$('#question .owner:not(#popup-close-question .owner)'),v=$('a',m);v.length&&(d='['+d+']('+u+v.attr('href')+')');var y=$('.relativetime',m);y.length&&(h=y.attr('title'));var w='[tag:'+c+'] [tag:'+f+'] '+p+' '+g+' - '+d+(h?'‭ - '+h:''),x='<textarea class=\'cvrg-result\' style=\'width:95%;display:block;margin:10px auto;\'>'+w+'</textarea>',T=$(x).appendTo(document.body),q='The text for your '+c;try{if(T[0].select(),!(e=document.execCommand('copy')))throw 1;var C='been copied to the clipboard.',O=q+' has '+C;l.show(O,483912),setTimeout(l.close,3e3,483912)}catch(t){var S=q+' is:',b=x,k='It has '+(e?'':'NOT ')+C;try{l.show(S+b+k+' You can press Ctrl-C now to copy it.',483912)}catch(t){alert(S+'\n\n'+w+'\n\n'+k)}}T.remove(),s.scrollTop(i),loopCount=0,setTimeout(function e(){loopCount++;var o=$('.cvrg-result');o.length?(o[0].select(),t()):loopCount<100?setTimeout(e,200):t()},200)}else t()}())



You can see the [non-minified version of the bookmarklet](SECloseVoteRequestGenerator-bookmarklet.js). 

For some reason, Edge does not permit directly creating bookmarklets. In Edge, you *must* import the bookmarklet from the [bookmarks file](SECloseVoteRequestGenerator-bookmarklet-bookmarks.html).  You will need to save that file to your system and then use Edge's settings->Import from another browser->Import from file.  You will probably then want to click on "View imported favorites" in order to move teh `cv-pls` bookmarklet to the location you desire.

Other browsers can also import from the .html file, but don't need to.
 

## Magic™ Editor

This is our own fork of the [Stack Exchange Editor Toolkit](http://stackapps.com/questions/4899/stack-exchange-editor-toolkit).

The Magic™ Editor _helps_ you make substantial edits to posts, by identifying and correcting many common mistakes. Ultimately, _you are responsible_ for your edits, so a key feature of the Magic™ Editor is a Diff Viewer, which is engaged automatically when you Invoke the Magic™.

### Installation
To install this script [click here](https://rawgit.com/SO-Close-Vote-Reviewers/UserScripts/master/Magic%E2%84%A2Editor.user.js) or otherwise visit the following URL, and Greasemonkey/Tampermonkey should ask you to install it.

     https://rawgit.com/SO-Close-Vote-Reviewers/UserScripts/master/Magic%E2%84%A2Editor.user.js
     
### Updates
This script uses the auto-update features of Tampermonkey / Greasemonkey. Your monkey will notify you usually within a couple of days when a new version becomes available.

To update manually you can visit the above URL again, or check for updates in Tampermonkey or Greasemonkey.

### Issues & enhancement requests
Before raising new issues, please review the [currently known issue list](https://github.com/SO-Close-Vote-Reviewers/UserScripts/labels/script%3AMagic%E2%84%A2%20Editor).

<!-- I used http://meyerweb.com/eric/tools/dencoder/ to encode the issue report template -->
To report a new issue or request an enhancement, create a GitHub Issue Report using [this template](https://github.com/SO-Close-Vote-Reviewers/UserScripts/issues/new?labels=script%3AMagic™%20Editor&body=**Script%3A**%20Magic%E2%84%A2%20Editor%0A**Issue%20type%3A**%20Bug%20%2F%20Enhancement%20%2F%20Auto-fix%20term%20request%20(pick%20one)%0A**Link%20to%20example%20post%3A**%20(where%20can%20the%20problem%20be%20reliably%20replicated%3F)%0A%0AIf%20you%20are%20requesting%20support%20for%20a%20new%20auto-correction%20term%2C%20explain%20why%20the%20rule%20should%20be%20supported.%20How%20prevalent%20is%20the%20mistake%3F%20For%20example%2C%20https%3A%2F%2Fregex101.com%2Fr%2FxN8qD9%2F1%20clearly%20shows%20what%20incorrect%20terms%20are%20expected%20to%20be%20addressed%2C%20and%20anticipates%20possible%20conflicts%2C%20as%20well%20as%20reporting%20on%20the%20number%20of%20existing%20posts%20containing%20the%20errors.) (requires a GitHub account).

As an alternative, you may send a Pull request for your own fixes or enhancements.

### User's guide

**REMEMBER:** Magic™ Editor is an editing aid, but **you** are responsible for your edits. Don't just click-and-go; always review your edits.

Rather than 2,000 words, here are two pictures to explain basic use.

The Magic™ wand appears on the editor tool bar when the Magic™ Editor is available for use.

![Magic™ wand](http://i.stack.imgur.com/jB5bR.png)

When you click the Magic™ wand, the display changes to show the applied updates in a diff view.

![After the Magic™](http://i.stack.imgur.com/2x6n7.png) 

#### Usage tips

**Before invoking the Magic™**, you should:
- Check that any code in the question is properly indented, so Magic™ Editor treats it as code, not prose.
- Likewise with any in-line code statements, which are best enclosed in backticks (`).

**Afterwards**, you should:
- _Review_ the results in the Diff view.
- Manually revert any automatic changes that were inappropriate for the current post. Consider these examples:
 - If [removal of tags from the title](http://meta.stackexchange.com/questions/19190/should-questions-include-tags-in-their-titles) made the title too short, you will need to [replace the entire title with a good one](http://meta.stackexchange.com/questions/10647/how-do-i-write-a-good-title).
 - Watch for undesired case changes, especially when the original post included any words in all-caps. (All Magic™ Editor spelling corrections are in lower case, except for the first character which remains as-is.)
- Note any mistakes that were missed; if they are common enough, you could report them as outlined earlier. (Rule of thumb: a "common" error will appear in at least a thousand posts on Stack Overflow, which is about 0.005% of them, OR occur daily.)

### Supported Corrections

At this time (4 Feb 2016), Magic™ Editor has:

- Rules for tidying question titles; tags are removed from the beginning and end, all caps titles are converted to Sentence case.
- 97 Trademark spelling & capitalization rules (e.g. "JavaScript", "MySQL", and "WordPress").
- 255 Spelling rules, many of which can fix multiple words.
- 55 Acronym capitalization rules (e.g. "HTTP")
- 25 Grammar rules addressing sentence capitalization, proper use of "a" vs. "an", spacing, comma usage, improperly formatted contractions ("Im", "ie", "eg", "etc", etc.), and common broken English (e.g. "I am wanting...").
- 12 Noise-reduction rules to remove fluff that adds nothing of technical value to posts.
- Automatic correction of numbered-list item layout.
- Editor support for shifting text (indent / outdent).

### Better handling of indentation and the TAB key when editing posts<sup>[ref](http://stackapps.com/questions/3247)</sup>
<sup><sub>Included script (c) 2012 Benjamin Dumke-von der Ehe, under [MIT Licence](https://opensource.org/licenses/MIT)</sub></sup>

This user script changes the behavior of a few keys (most notably the <kbd>Tab</kbd> key) within the post editor to behave more like it does in IDEs or text editors:

* When one or more lines are selected, <kbd>Tab</kbd> and <kbd>Shift</kbd>-<kbd>Tab</kbd> indent and outdent these lines

* When nothing is selected, <kbd>Tab</kbd> and <kbd>Shift</kbd>-<kbd>Tab</kbd> insert or remove whitespace to align the cursor on a tab boundary

* When the cursor is within the left margin of a line, <kbd>Backspace</kbd> removes whitespace to align the cursor on a tab boundary (in other words, it may delete more than just one space character)

* On indented lines, the <kbd>Home</kbd> key toggles the cursor between the *actual* beginning of the line and the beginning of the real content (in other words, it jumps back and forth to before and after the leading whitespace). This only happens on lines that are indented by at least four spaces or a tab, since it can be confusing for the following reason: When you press <kbd>Home</kbd> in the text editor, you expect the cursor to jump to the beginning of the line *as it is displayed*, which (due to wrapping) may be different from the actual previous newline character.

* So that you don't have to reach for the mouse to tab out of the editor, you can press *and release* the <kbd>Ctrl</kbd> key, and the next key press will not be intercepted; thus <kbd>Tab</kbd> takes you out of the editor. Pressing and releasing <kbd>Ctrl</kbd> will grey out the text editor until the next keystroke to clarify this. If you think this is too awkward, I'm open to other suggestions, but there should be some way to tab out of the editor .

Note that this will never insert TAB characters, only spaces. It does however handle already-present TABs, and it handles them the same way the Markdown converter does.
