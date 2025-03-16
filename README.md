| INFO PROPERTY | VALUE                                                |
| ------------- | ---------------------------------------------------- |
| Program Name  | **EHW TUTWRK: Traversy Site Clone: Netflix** |
| Project Type  | HTML5 Site Clone                                      |
| File Name     | README.md                                            |
| Date Created  | 03/16/2025                                           |
| Date Modified | --                                                   |
| Version       | 00.00.01                                             |
| Programmer    | **Eric Hepperle**                                    |

### GITHUB REPO

- https://github.com/codewizard13/ehw-tut-trav-site-clone-netflix

### TUTORIAL NOTES

- [notes/index.md](/notes/index.md) [_There's actually NO NOTES yet_]

### TECHNOLOGIES

<img align="left" alt="WordPress" title="WordPress" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/wordpress/wordpress-original.svg" style="padding-right:10px;" />

<img align="left" alt="HTML5" title="HTML5" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" style="padding-right:10px;" />

<img align="left" alt="CSS3" title="CSS3" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" style="padding-right:10px;" />

<img align="left" alt="JavaScript" title="JavaScript" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" style="padding-right:10px;" />

<img align="left" alt="PHP" title="PHP" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" style="padding-right:10px;" />

<img align="left" alt="MySQL" title="MySQL" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg" style="padding-right:10px;" />

<img align="left" alt="Git" title="Git" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" style="padding-right:10px;" />

<img align="left" alt="GitHub" title="GitHub" width="26px" src="https://user-images.githubusercontent.com/3369400/139448065-39a229ba-4b06-434b-bc67-616e2ed80c8f.png" style="padding-right:10px;" />


<br>

## SCREENSHOTS

**PROGRESS 03-16-2025:  STOPPED @ 20:06 after create sign in btn**

![PROGRESS 03-16-2025:  STOPPED @ 20:06 after create sign in btn](/img/screens/tut-progress-001.png)

## CODE

**_Heres a code snippet I created with the help of Perplexity AI that lets me display and use ACF fields as custom dynamic tags in WPForms_**

- Add to functions.php or a custom plugin

```php
/**
 * Summary of dynamic_acf_smart_tags:
 * 
 * - Not sure why this works, but it does. Perplexity AI helped.
 * @param mixed $tags
 * 
 * Ref:
 * - https://www.perplexity.ai/search/i-m-trying-to-include-an-acf-c-bDVrWF9dQamDSSUNDcJonA
 */
function dynamic_acf_smart_tags($tags) {
	$tags['acf_field'] = 'ACF Field';
	return $tags;
}
add_filter('wpforms_smart_tags', 'dynamic_acf_smart_tags');

function process_dynamic_acf_smart_tags($content, $tag) {
	if (strpos($tag, 'acf_field_') === 0) {
			$field_name = str_replace('acf_field_', '', $tag);
			$field_value = get_field($field_name, get_the_ID());
			$content = str_replace('{acf_field_' . $field_name . '}', $field_value, $content);
	}
	return $content;
}
add_filter('wpforms_smart_tag_process', 'process_dynamic_acf_smart_tags', 10, 2);
```

### functions.php snippet: PHPMailer - to send email without needed a plugin

```php

// PHP MAILER SMTP OVERRIDE
// REF: https://github.com/PHPMailer/PHPMailer/
//     https://www.youtube.com/watch?v=YtNraQxUTM0
//
// NOTE: SMTP_LOGIN, SMTP_PASSWORD are defined in wp-config.php
//
add_action('phpmailer_init','custom_mailer');
function custom_mailer( PHPMailer $phpmailer ) {

	
	$from_email = 'noreply@yoursite.com';
	$from_name = 'Your Site No-Reply';
	$host = 'smtp.your-isp-server.com';
	$port = 587;
	$smtp_secure = 'tls';


	// $mail_body = '<p><strong>Hello!</strong> This is an email sent with PHPMAILER</p>';

	// SMTP / Server Settings

	// $phpmailer->SMTPDebug = 2;
	$phpmailer->SetFrom($from_email, $from_name);
	$phpmailer->Host = $host;
	$phpmailer->Port = $port;
	$phpmailer->SMTPAuth = true;
	$phpmailer->SMTPSecure = $smtp_secure;
	$phpmailer->Username = SMTP_LOGIN;
	$phpmailer->Password = SMTP_PASSWORD;
	$phpmailer->isSMTP();

	// $phpmailer->isHTML(true);
	// $phpmailer->Subject = $phpmailer->Subject . ' - EXTRA SUBJECT PART!';
	// $phpmailer->Body = $phpmailer->Body . $mail_body . '<br>This is a <b>SIGNATURE</b><br>';
	// $phpmailer->AltBody = strip_tags($mail_body);

}
```


## TAGS

`Tutwrk` `WordPress` `WordPress Themes` `Themes from Scratch` `Eric Hepperle` `Mr Digital` `WordPress Classic Theme` `WPForms` `Forms Plugin` `PHPMailer` `PHP Mail` `WordPress Email`


## PURPOSE

This is a custom PHP theme with sidebar on the Right. [Following MrDigital's excellent tutorial]

## REFERENCES

- [WordPress Theme Development From Scratch](https://www.youtube.com/watch?v=n3EcEYFgyrQ&list=PLgFB6lmeXFOpHnNmQ4fdIYA5X_9XhjJ9d)
- [WordPress Tutorial 1: Introduction](https://www.youtube.com/watch?v=8OBfr46Y0cQ&list=PLpcSpRrAaOaqMA4RdhSnnNcaqOVpX7qi5)
- [How to convert an HTML Template to a WordPress Theme (2019)](https://www.youtube.com/watch?v=FN5jhyspVXc)