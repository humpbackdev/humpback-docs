# ahoy site install-from-db

This command could be executed as many times as needed and it allows you to set up your local site based on a db backup.
If you don't have a db backup yet, it will try to download one from the Pantheon live environment using Terminus. If you don't have an integration with Pantheon or you just want to supply the database backup manually, you'll have to put in the root directory of the project the compressed backup under the name `<your project name>.sql.gz`.
This command will:

- Get the compressed database backup if it doesn't exists.
- Uncompress the backup and import it in the database.
- Run database updates.
- Import configuration.
- Clear caches.
- Sanitize the database.
