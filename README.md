# Drupal upgrade the easy way
Drupal upgrade the easy way - More Information @ https://fuerstnet.de/en/drupal-upgrade-easy-way

---

### **2015-10-15**: Upgraded patch files to Drupal 7.40. 
Take care: `.htaccess` and `sites/default/default.settings.php` got changes. Make sure you have a backup of your `.htaccess` before applying the patch. If you modified your `.htaccess` before the patch may not apply. In this case rename your `.htaccess` to `.htaccess-mine` and apply the patch. It will ask you which file to patch, just press ENTER. Now it asks if you want to skip this patch. Enter "y" and press ENTER. Rename `.htaccess-mine` back to `.htaccess` and apply the changes to `.htaccess` as described in Release notes for 7.40). Also have a look there what did change in the `settings.php`.

---

The standard procedure to upgrade Drupal to the latest release is to download it from drupal.org and follow the included UPGRADE.txt.

For administrators using the UNIX shell it may be easier using the attached patch files below instead of downloading and installing the newest complete Drupal release.


## Usage

To patch your Drupal installation follow UPGRADING.txt up to and including

- for Drupal 6.5: Disable all custom and contributed modules.
- for Drupal 7.2: Go to Administration > Configuration > Development > Maintenance mode...

Now go on using this commands:

* `cd DRUPAL-ROOT`
* Dry run for testing without modifying anything: `patch -p1 --dry-run < PATCHFILE`
* Do the real patching: `patch -p1 < PATCHFILE`

Your Drupal installation is now upgraded. proceed with UPGRADING.txt from

* for Drupal 6.9: Verify the new configuration file to make sure it has correct information.
* for Drupal 7.5: Re-apply any modifications to files such as .htaccess or robots.txt.

## **Warning**
  If you get errors like
  `Reversed (or previously applied) patch detected` or `1 out of 2 hunks FAILED`
  while running the patch dry run (second command above) immediately interrupt patching and upgrade following the steps explained in UPGRADING.txt.

Use this patch files on your own responsibility. I don't guarantee the proper function of the patch files on Drupal installations other than my own.


###Note:
If the patch process gets interrupted and leaves a mix of patched and unpatched files you may re-run it by ignoring already patched files after eliminating the reason of the interruption:

* `patch -p1 -N < PATCHFILE`

You may savely remove reject files created during that process:

* `find . -name "*.rej" | xargs rm`
* 
