# Lichess Puzzle Playthrough script

It's TamperMonkey script. But it can be converted into Chrome/Firefox extension too, because it doesn't use any Web Extensions API at all.

The script allows you to click "next" button
at the end of the puzzle to play the current
position versus computer.

Works with Lichess Web interface (2025).

The engine is lously callibrated and plays at the level about equal to your current puzzle rating.

The engine used is lozza.js v2.5 (max ELO ~ 2000-2500).

Extra features:

* The script changes GUI a bit to make it look more like new official Android client. If you don't like it you can comment `appendChild` command, which adds all the styling.
* Click on your rating to show current evalution of the position
* Evaluation of the position of the puzzle end is automatically shown
* Automatically move to the next puzzle if the puzzle ends with checkmate


## TamperMonkey notes:

To install the script use **Utilities** - Import from file.
* You might need to disable Firefox's `security.csp.enable` because of
https://github.com/Tampermonkey/tampermonkey/issues/700.
* See also https://github.com/Tampermonkey/tampermonkey/issues/952#issuecomment-638373937 for another workaround.
* The problem is that the script inserts its code using `appendChild` and new versions of Firefox seem to disallow it when site's CSP policy is configured.
* So you might need to change the option **Security** - Modify existing content security policy (CSP) headers: to `Remove enirely`
* Also you might need to switch TM script execution mode to "Instant"
because this script needs to be executed very early to be able to simulate
chessboard clicks. (**Experimental** - Inject Mode -`Instant`)
* To make these changes you need to switch to advanced config mode: **General** - Config mode - `Advanced`.
