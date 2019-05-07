### IntelliJ IDEA

If you're working on this project, setup IntelliJ to automatically follow the consistent and enforced style.

* Install the Checkstyle plugin
    * IntelliJ IDEA -> Preferences...
    * Plugins
    * Search "CheckStyle-IDEA"
    * Install and restart
* Setup the Checkstyle plugin
    * IntelliJ IDEA -> Preferences...
    * Other settings, Checkstyle
    * Add (+) Configuration File
        * Description: Google
        * File: $PROJECT_DIR/google_checks.xml
* Change project Code style
    * IntelliJ IDEA -> Preferences...
    * Editor, Code Style
    * Scheme: Project
    * Gear: Import Scheme -> CheckStyle configuration
        * File: $PROJECT_DIR/google_checks.xml
* Setup import order
    * IntelliJ IDEA -> Preferences...
    * Editor, Code Style, Java
    * Imports tab
        * Use single class import: Check
        * Class count to use import with '*': 99
        * Names count to use static import with '*': 99
        * Packages to Use Import with '*': Remove all rows
        * Layout static imports separately: Check
        * Import Layout:
            * import static / all other imports
            * <blank line>
            * import / all other imports
            * <blank line>
* Enable optimize import on reformat
    * Open a Java file
    * Code -> Show Reformat File Dialog
    * Check Optimize Imports
* Don't remove blank lines
    * IntelliJ IDEA -> Preferences...
    * Editor, Code Style, Properties
    * Check Keep blank lines
        
### Build Reports

* Checkstyle report in build/reports/checkstyle
* Jacoco coverage report in build/reports/jacoco