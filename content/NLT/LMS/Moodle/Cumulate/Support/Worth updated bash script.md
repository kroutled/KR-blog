## healthy-company-learners-no-auth-filter.csv report: 
```sh
mysql --user=${MYSQL_USER} --password=${MYSQL_PASSWORD} --database=${MYSQL_DATABASE} --host=${MYSQL_HOSTNAME} -e "SELECT UUID() AS 'UID',
user.idnumber AS 'entity number',
COALESCE((SELECT MAX(mdl_user_info_data.data) FROM mdl_user_info_data JOIN mdl_user_info_field ON mdl_user_info_field.id = mdl_user_info_data.fieldid
        WHERE mdl_user_info_data.userid = user.id AND mdl_user_info_field.shortname = 'idnumber'), '') AS 'ID Number',
user.firstname, user.lastname, user.email, user.auth AS 'auth type',
COALESCE((SELECT MAX(mdl_user_info_data.data) FROM mdl_user_info_data JOIN mdl_user_info_field ON mdl_user_info_field.id = mdl_user_info_data.fieldid
        WHERE mdl_user_info_data.userid = user.id AND mdl_user_info_field.shortname = 'group'), '') AS 'hc company',
course.id AS 'course id', course.fullname AS 'course name',
IF(course_completions.timestarted = '0', '', FROM_UNIXTIME(course_completions.timestarted, '%Y-%m-%d')) AS 'date started',
IF(course_completions.timecompleted = '0', '', FROM_UNIXTIME(course_completions.timecompleted, '%Y-%m-%d')) AS 'date ended',
IF(user_enrolments.timecreated = '0', '', FROM_UNIXTIME(user_enrolments.timecreated , '%Y-%m-%d')) AS 'date enrolled'
FROM mdl_user user
INNER JOIN mdl_user_enrolments user_enrolments ON user_enrolments.userid = user.id
LEFT JOIN mdl_enrol enrol ON enrol.id = user_enrolments.enrolid
INNER JOIN mdl_course course ON course.id = enrol.courseid
LEFT JOIN mdl_course_completions course_completions ON course_completions.userid = user.id AND course.id = course_completions.course
WHERE (course.id = '9' OR course.id = '30' OR course.id = '8' OR course.id = '17' OR course.id = '12' OR course.id = '14' OR course.id = '15' OR course.id = '31' OR course.id = '16' OR course.id = '38' OR course.id = '13' OR course.id = '36' OR course.id = '19' OR course.id = '34' OR course.id = '32' OR course.id = '35' OR course.id = '18' OR course.id = '33' OR course.id = '11');" | sed 's/\t/","/g;s/^/"/;s/$/"/;s/\n//g' > /var/www/reports/report.csv

```

## healthy-company-learners-no-auth-filter-daily.csv
```sh
mysql --user=${MYSQL_USER} --password=${MYSQL_PASSWORD} --database=${MYSQL_DATABASE} --host=${MYSQL_HOSTNAME} -e "SELECT UUID() AS 'UID',
user.idnumber AS 'entity number',
COALESCE((SELECT MAX(mdl_user_info_data.data) FROM mdl_user_info_data JOIN mdl_user_info_field ON mdl_user_info_field.id = mdl_user_info_data.fieldid
        WHERE mdl_user_info_data.userid = user.id AND mdl_user_info_field.shortname = 'idnumber'), '') AS 'ID Number',
user.firstname, user.lastname, user.email, user.auth AS 'auth type',
COALESCE((SELECT MAX(mdl_user_info_data.data) FROM mdl_user_info_data JOIN mdl_user_info_field ON mdl_user_info_field.id = mdl_user_info_data.fieldid
        WHERE mdl_user_info_data.userid = user.id AND mdl_user_info_field.shortname = 'group'), '') AS 'hc company',
course.id AS 'course id', course.fullname AS 'course name',
IF(course_completions.timestarted = '0', '', FROM_UNIXTIME(course_completions.timestarted, '%Y-%m-%d')) AS 'date started',
IF(course_completions.timecompleted = '0', '', FROM_UNIXTIME(course_completions.timecompleted, '%Y-%m-%d')) AS 'date ended',
IF(user_enrolments.timecreated = '0', '', FROM_UNIXTIME(user_enrolments.timecreated , '%Y-%m-%d')) AS 'date enrolled'
FROM mdl_user user
INNER JOIN mdl_user_enrolments user_enrolments ON user_enrolments.userid = user.id
LEFT JOIN mdl_enrol enrol ON enrol.id = user_enrolments.enrolid
INNER JOIN mdl_course course ON course.id = enrol.courseid
LEFT JOIN mdl_course_completions course_completions ON course_completions.userid = user.id AND course.id = course_completions.course
WHERE (course.id = '9' OR course.id = '30' OR course.id = '8' OR course.id = '17' OR course.id = '12' OR course.id = '14' OR course.id = '15' OR course.id = '31' OR course.id = '16' OR course.id = '38' OR course.id = '13' OR course.id = '36' OR course.id = '19' OR course.id = '34' OR course.id = '32' OR course.id = '35' OR course.id = '18' OR course.id = '33' OR course.id = '11') AND FROM_UNIXTIME(user_enrolments.timecreated , '%Y-%m-%d %h:%i:%s') BETWEEN DATE_SUB(NOW(), INTERVAL 1 DAY) AND NOW();" | sed 's/\t/","/g;s/^/"/;s/$/"/;s/\n//g' > /var/www/reports/report.csv

```