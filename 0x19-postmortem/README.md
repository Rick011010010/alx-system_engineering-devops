Issue Overview
Following the rollout of a fresh feature on our newly launched Python Flask platform, we encountered our inaugural wave of users expressing grievances about the platform's functionality. Barely 5 minutes post-update, our inbox started flooding with messages from users reporting difficulties in logging in or registering on our service. This development caught us off guard, as the feature had been thoroughly tested and was functional on our local environments and prior to deployment. Approximately 127 such complaints inundated our inbox, prompting immediate action. Aware of the significance of user retention, we swiftly delved into investigating the issue. Cloning the repository from GitFlaw and adhering to the installation guidelines in the README, we were startled to find that the platform failed to launch. It didn't take long to identify the root cause: neglecting to update the project's prerequisites. The platform experienced dysfunction from 9:55 AM GMT+1 to 11:20 AM GMT+1.

Chronology
05-02-2022 9:55 AM GMT+1 - Initial report from a user unable to log in.
05-02-2022 10:20 AM GMT+1 - Backend developer Winus encountered the same login issues.
05-02-2022 10:35 AM GMT+1 - Investigation commenced into controller and view inconsistencies.
05-02-2022 10:40 AM GMT+1 - Suspicions arose regarding the bcrypt gem, suspecting either incorrect usage or malfunction.
05-02-2022 10:42 AM GMT+1 - Inspection disproved assumptions regarding form field bindings.
05-02-2022 10:45 AM GMT+1 - Controller operations were scrutinized for potential hash discrepancies.
05-02-2022 10:50 AM GMT+1 - Winus speculated on improper password hashing.
05-02-2022 11:00 AM GMT+1 - Issue escalated to the backend development team.
05-02-2022 11:20 AM GMT+1 - Problem resolved by updating backend server requirements (bcrypt gem version).

Root Cause and Fix
The outdated version of the bcrypt gem triggered errors regarding seemingly valid hashes, likely due to compatibility issues. Winus rectified the situation by manually updating the bcrypt version in the Gemfile.lock to a more recent iteration, followed by reinstallation of the required gems.

Corrective and Preventative Actions
Implement a continuous integration pipeline to execute builds on each pull request branch, ensuring successful builds before merging with the deployment branch.
Deploy a monitoring system for both database and application servers to promptly detect and address any arising issues.
Establish comprehensive tests for new features, mandating their passage before merging with the deployment branch.
