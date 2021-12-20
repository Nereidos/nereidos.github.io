
# Upgrade Notice
> Always update to the latest minor update before updating a major version (for example: if on 21.0.0 first upgrade to 21.0.7 before upgrading to 22.2.3)
> In Minor updates you can jump to the latest (for example from 22.0.0 to 22.2.0)

---

# Upgrade 
- Enable maintance mode
```
sudo -u <www-data> php /var/www/<nextcloud>/occ maintenance:mode --on
```
- Rename Oldversion
```
sudo mv /var/www/<nextcloud> /var/www/<nextcloud>_oldver
```
- Download the new Nextcloud Version [from HERE](https://nextcloud.com/changelog/)
```
wget https://download.nextcloud.com/server/releases/nextcloud-<latest>.tar.bz2
```
- Extract (Unzip) Tar Bz2 File
```
tar -xvf nextcloud-<VERSION>.tar.bz2
```
- Rename (same name as the old version) and move the new version
```
sudo mv <nextcloud>/ /var/www/
```
- Copy the config.php file from the Old to the new version
```
sudo cp -av /var/www/<nextcloud>_oldver/config/config.php /var/www/<nextcloud>/config/
```
- Grand rights
```
sudo chown -R <www-data>:<www-data> /var/www/<nextcloud>
```
- Check Status before upgrade
```
sudo -u <www-data> php /var/www/<nextcloud>/occ status
```
- Run OCC upgrade script
```
sudo -u <www-data> php /var/www/<nextcloud>/occ upgrade
```
- Check app:list
```
sudo -u www-data php /var/www/nextcloud/occ app:list
```
- Disable maintenance:mode
```
sudo -u <www-data> php /var/www/<nextcloud>/occ maintenance:mode --off
```
- Check for error's in Nextcloud Web Overview
