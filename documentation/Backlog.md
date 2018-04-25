# Backlog/Future Work

Here we outline the backlog of future work and improvements we've been documenting throughout development. Because this project was made over the course of a single semester by a small team, we necessarily had to cut many features and opt for simple solutions in lieu of proper solutions (lest the perfect be the enemy of the good).

Below is the list of features the original authors have identified as backlog features, in order of priority for future development.

1. **Responsive Web Design**
   The web app currently is completely unusable on mobile or tablet. This was a feature cut because our target users did not necessarily have mobile data plans, and the form design was quite complicated even on desktop. However, transferring photos from mobile devices to computers is difficult and some users will have access to mobile data, so a responsive website is a necessary first step to improve the project.
2. **Web Security**
   None of the original authors are experts in web security, and therefore included only off-the-shelf web security solutions. They used helmet, sanitization/validation and a password to prevent the most basic of attacks, but it's quite important to consult with someone familiar with web security practices to plug all gaps left.
3. **Excel Powered Data Visualization**
   While it was not the original reason we selected Sheets, given that we are using Sheets as our database, we should take advantage of it. Sheets makes use of Excel-like graphing and data analysis features, so some proper thought should go into how the end-user analyzes and graphs the gathered data.
4. **Support Video Uploads**
   The volunteer we worked with to design this tool suggested at one point that uploading videos would be useful for certain types of violations or other hazards, like overflowing sewer drains. We could support video uploads in largely the same way we support photo uploads.
5. **Refactor to only use Google's official API** 
   We're currently using two npm packages for communicating with Google. This occurred because the original Google Sheets module we installed did not support Google Drive. However, we think that making use of only the official Google Node Client will be more stable in the long run than a 3rd party Google Sheets module.
6. **Setup React to Support Paths**
   We originally built this app using React-Router, but learned on deployment that we couldn't' directly link to paths, even if React-Router displayed paths in the URL on the browser. Given the nature of React, we should have known better. However, we quickly removed React-Router to avoid confusion. 
   We do think that it would be useful for the site to support paths though, and see two ways to approach that problem. Server-side rendering of our react app, or using multiple react apps per screen.
7. **Public-Accessible Data Visualization**
   There is already an underlying need for the public website to display data from Sheets, not just upload it. We had to cut this feature to complete data uploading, but thought should go into how this would work. 
   We have a direction worth considering for this feature as well. During every testing period, users cited a desire to see outstanding and resolved *violations*, not houses. Note that we record data based on address-first, but users think violation-first. This doesn't preclude recording data house-first (meaning data is primarily categorized by address) but it does suggest that users would expect to see lists of violations on the website. This makes sense if you consider if from a few plausible user stories. 
   *"I've noticed a boarded-up home near my house. Has this issue been reported?"*
   "*I submitted a notice of the boarded-up home. How's that issue coming along?*"
8. **Form Address Picker w/ Google Maps**
   It's a noted issue with our form that selecting an address is cumbersome and will not scale. This is due to three underlying factors
   First, camera's and phones use random filenames, or timestamps. Matching photos taken in the field with addresses from paper forms is difficult
   Second, it's quite possible that the person uploading information from paper forms will not be the person who actually filled out the form or took pictures.  They will therefore not even be able to match photos with pictures from memory
   Third, our current system uses a dropdown to assist users with spelling known addresses properly. This will fail if a large number of addresses are used however, as the dropdown will become unreasonably long. A different method of input may work (search vs. dropdown) but ideally we create a way to added addresses using a map-based interface. Furthermore, many phones and cameras use EXIF metadata attached to jpgs, which can contain GPS coordinates. Taking advantage of that with a map interface for address selection is the ideal case.
9. **Export feature for specific house/issue**
   The question of how to share data came up a few times. We would answer by citing the fact that excel is reasonably user-friendly and one could copy-paste specific rows if one wanted to share subsets of our data. However, designing an automated way to search for a given category of code violation or address and pull just that data could still be made. This could be done in Sheets scripting or on the node server.
10. **Real Database**
   This is a debatable idea, but we suggest that eventually this project should make use of a real database. Which system is also up for consideration, but we see two reasons that this shift should happen
   First, storing photos on Drive and updating them is complex and requires string manipulation. Sheets cannot embed photos or other media, so we resorted to storing links to photos in Sheets and using a naming schema to identify photos. This is hard to read and edit post facto though.
   Second, different people will likely want to approach the data from different angles. Residents, for example, will likely be concerned about issues, and want to look up specific ones. City officials will likely be concerned with the data at the house or lot level. These different approaches suggest that a database with a strong query language would be useful, so that we can pull relevant datasets based off individual uses.
   This isn't without cost. We designed this system with Sheets in mind so non-expert users could review our data. If we switched to a true database, we would need to replicate some of that functionality ourselves or somehow make it easy to export data, as we anticipate the need to keep non-expert users in the loop won't be going away.

