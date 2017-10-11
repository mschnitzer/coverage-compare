# OBS Coverage Comparing Tool
Compares two coverage reports and creates cards for each file which differs.

This tool was created for the Open Build Service project to compare which files are not properly covered by tests in our new testsuite but were covered in the old one.

## Usage
1. (Skip if you already have a `settings.json` file): Run the script (without any parameters) once
2. Adjust the `settings.json` file with your trello API credentials. (see below for more information)
3. Visit https://codecov.io/gh/openSUSE/open-build-service
4. Click the latest commit
5. Click the "Build" tab
6. Download the `#rspec` and `#api` (minitest test suite) test results
7. Copy the commit hash to the clipboard (see current URL)
8. Run the script: `./compare_coverage_reports.rb [Commit-Hash] [rspec_results_file] [api_results_file]`
9. Look at the Trello board you specified in the `settings.json` to view if it's working

`settings.json` Notes:
* `trello_board` must have the ID to the trello board. The ID can be fetched via Trello's API:
   ```
   curl 'https://api.trello.com/1/members/$YOUR_TRELLO_USER/boards?key=$YOUR_TRELLO_API_KEY&token=$YOUR_TRELLO_API_TOKEN'
   ```
* The Trello API credentials can be found here: https://trello.com/app-key
