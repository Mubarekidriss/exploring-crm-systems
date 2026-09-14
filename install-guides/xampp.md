# SuiteCRM XAMPP Guide - Windows Manual Route

This route uses **SuiteCRM 7.14.9** because the current XAMPP Windows package supplies PHP 8.2 and MariaDB 10.4. SuiteCRM's official compatibility matrix lists PHP 8.1/8.2 and MariaDB 10.4 for the 7.14 line. Do not switch to a different SuiteCRM or XAMPP version without checking the matrix again.

## Time target

Allow about 25-40 minutes if XAMPP downloads and starts normally.

## 1. Install XAMPP 8.2.12

Download the Windows PHP 8.2.12 package from:

https://www.apachefriends.org/download

Install to the default folder:

```text
C:\xampp
```

Open **XAMPP Control Panel** and start **Apache** and **MySQL**. Both rows should turn green.

## 2. Enable/check PHP extensions

In XAMPP Control Panel, next to Apache choose **Config > PHP (php.ini)**. Search for these lines. Remove the leading semicolon if present:

```ini
extension=curl
extension=gd
extension=intl
extension=mbstring
extension=mysqli
extension=openssl
extension=pdo_mysql
extension=soap
extension=zip
```

Also set:

```ini
memory_limit=512M
upload_max_filesize=64M
post_max_size=64M
max_execution_time=300
```

Save the file and restart Apache.

## 3. Download the pinned SuiteCRM package

Download `SuiteCRM-7.14.9.zip` from the official release:

https://github.com/SuiteCRM/SuiteCRM/releases/tag/v7.14.9

Extract it. Rename the extracted application folder to `suitecrm` and place it here:

```text
C:\xampp\htdocs\suitecrm
```

Check that this file exists:

```text
C:\xampp\htdocs\suitecrm\index.php
```

Do not accidentally create an extra nested folder such as `suitecrm\SuiteCRM-7.14.9\index.php`.

## 4. Create the database

Open:

http://localhost/phpmyadmin

1. Select **Databases**.
2. Create a database named `suitecrm`.
3. Use collation `utf8mb4_general_ci` if it is offered.

For a local class-only setup, the default XAMPP database user is normally:

- Host: `localhost`
- User: `root`
- Password: leave blank
- Database: `suitecrm`

Never use an empty root password on a public or production server.

## 5. Run the installer

Open:

http://localhost/suitecrm

Follow the installer:

1. Accept the license.
2. Wait for the system check.
3. Choose MySQL/MariaDB.
4. Enter the database settings above.
5. Create the SuiteCRM administrator:
   - Username: `admin`
   - Password: create a new local-only password
   - Email: `mubarekidris.r@gmail.com`
6. Finish installation and sign in.

If the system check shows a missing PHP extension, enable the named extension in `php.ini`, restart Apache, and reload the check. Do not skip a required extension.

## 6. Create safe sample records

Use made-up class data only.

1. Create Contact `Jordan Lee`, email `jordan@example.test`.
2. Create Lead `Taylor Morgan`, company `North Star Demo`.
3. Add an Opportunity if the dashboard needs sample data.
4. Add a Leads or Opportunities dashlet to the dashboard if needed.
5. Open **Reports**, create a basic Leads report, and display a table or chart.

## 7. Capture the five screenshots

Save real PNG files using these exact names:

- `login.png`
- `dashboard.png`
- `contacts.png`
- `leads.png`
- `reports.png`

Replace the five placeholders in `screenshots/`. Keep the page title visible and do not expose the password, real customer data, bookmarks, or unrelated tabs.

## 8. Finish the worksheet

Replace every bracketed field in `open_source_evaluation.md` with your real observations and check the screenshot list.

## Troubleshooting

### Apache will not start

Port 80 may be used by IIS, another web server, or another application. Check the XAMPP log first. The simplest fix is usually to stop the conflicting service. If Apache must use another port, update its `Listen` setting and open the matching URL, such as `http://localhost:8080/suitecrm`.

### MySQL will not start

Do not delete database files. Read the MySQL error log from XAMPP Control Panel. Another MySQL service may already be using port 3306.

### Blank page or 500 error

Read:

```text
C:\xampp\apache\logs\error.log
C:\xampp\htdocs\suitecrm\suitecrm.log
```

Confirm the PHP version and required extensions. Use the exact error message rather than applying random fixes.

### Installer cannot connect to database

Confirm MySQL is green in XAMPP, the database is named `suitecrm`, the host is `localhost`, and the username/password match phpMyAdmin.

### Reports menu is not visible

Use the main module menu and look for **Reports**. If needed, use the menu configuration to expose the module. The official SuiteCRM documentation confirms that Reports is a built-in module.

## Cleanup

This is a local evaluation. Stop Apache and MySQL in XAMPP Control Panel when finished. Do not upload the CRM installation or database to the assignment repository. Only the report, diagram, guide, and screenshots belong in GitHub.
