# Using a different installation profile

Humpback by default creates an installation profile specific for the generated project, that profile is stored in `profiles` folder and its content is symlinked to the folder `web/profiles/custom`. This profile is used by default to install the site.
If you want to override this behavior and use a different install profile (custom or contrib), you'll need to place that profile in the right folder (profiles/custom) or you can add it to the project using `composer require` and ensuring it gets placed under web/profiles/contrib and then make some small changes to ensure that profile gets used:

- Remove all config files under `config/sync` to ensure profile config is used
- Change install profile on .ahoy/site.ahoy around **line 58**:
```bash
ahoy drush site-install <profile_name> --account-pass=admin -y
```
- Change install profile on `settings/settings.php` around **line 41**:
```php
$settings['install_profile'] = <profile_name>;
```
- Change install profile in circleci build job install command around **line 46** `../vendor/bin/drush si <profile_name>` (it's twice in the same line)
- Change install profile in circleci deploy job install command around **line 120**:
```bash
terminus drush <profile_name>.dev -- si <profile_name> --account-pass=admin -y
```


And that's all!

By doing this, once you run `ahoy site install` command, your desired profile will be used and then you'll be able to export the config and continue using your project as you'd normally do.
