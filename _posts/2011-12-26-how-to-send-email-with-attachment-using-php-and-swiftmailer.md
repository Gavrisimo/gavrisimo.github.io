---
title: How to send email with attachment using php and swiftmailer?
author: Miloš Gavrilović
layout: post
permalink: /how-to-send-email-with-attachment-using-php-and-swiftmailer/
categories:
  - PHP
  - Tips
---
If you have some contact form(or just any form) where you need to have &#8216;upload file' field(s) and you must do that in PHP &#8211; this article might help you.

Almost every tutorial I found while googling for a solution is a lot of spaghetti code. That's why I decided to use swiftmailer, which makes code pretty self explanatory &#8211; so dig in.

Library used is <a title="http://swiftmailer.org/" href="http://swiftmailer.org/" target="_blank">swiftmailer</a> which you need to <a title="http://swiftmailer.org/download" href="http://swiftmailer.org/download" target="_blank">download</a> and upload to your server. Also it has with <a title="http://swiftmailer.org/docs/introduction.html" href="http://swiftmailer.org/docs/introduction.html" target="_blank">excellent docs</a>.

<pre class="brush: php; title: ; notranslate" title="">require_once 'swiftmailer/swift_required.php';

if ( // Maybe add some validation here, like check for value of some hidden field or whatever ) {

    // Catch your $_POST
    $yourName = $_POST['yourName'];
    // etc

    // File validation
    $maxFileSize = 10240; // file size in KB
    $maxFileSizeMb = $maxFileSize / 1024; // file size in MB

    // Specify what extension you are accepting for your file
    $allowedExtensions = array("jpg", "jpeg", "tiff", "pdf", "doc", "docx");

    $uploadedFileName = basename($_FILES['yourFile']['name']);
    $uploadedFileType = substr($uploadedFileName, strrpos($uploadedFileName, '.') + 1);
    $uploadedFileSize = $_FILES["yourFile"]["size"] / 1024;

    if ( $uploadedFileSize &gt; $maxFileSize ) {
        $errors .= "Size of file should be less than $maxFileSizeMb MB rn";
    } else {
        $extensionAllowed = false;

        for ( $i = 0; $i &lt; sizeof($allowedExtensions); $i++ ) {
            if ( strcasecmp($allowedExtensions[$i], $uploadedFileType) == 0 ) {
                $extensionAllowed = true;
            }
        }

        if ( ! $extensionAllowed ) {
            $errors .= "The uploaded file is not supported file type. Only the following file types are supported: " . implode(',',$allowedExtensions) . " rn";
        } else {
            $pathOfUploadedFile = "some-writable-directory/$uploadedFileName";

            $tmp_path = $_FILES["yourFile"]["tmp_name"];

            if ( is_uploaded_file($tmp_path) ) {
                if( ! copy($tmp_path, $pathOfUploadedFile) ) {
                    $errors .= "error while copying the uploaded file rn";
                } else {
                    // Set up message text
                    $messageText = "Name: $yourName rn";
                    // etc

                    // Start up swiftmailer
                    $transport = Swift_MailTransport::newInstance();

                    //Create the Mailer using your created Transport
                    $mailer = Swift_Mailer::newInstance($transport);

                    //Create a message
                    $message = Swift_Message::newInstance("Your name: $yourFullName")
                      -&gt;setFrom(array($yourEmail =&gt; $yourFullName ) )
                      -&gt;setTo(array("mail@mail.com" =&gt; "John Doe"))
                      -&gt;setBody($messageText)
                      -&gt;attach(Swift_Attachment::fromPath( $pathOfUploadedFile ));

                    //Send the message
                    if( $mailer-&gt;send($message) ) {
                        // if mail has been sent -&gt; delete uploaded file from your server
                        unlink($pathOfUploadedFile);
                    }
                }
            } else {
                $errors .= "tmp_path fail rn";
            }
        }
    }

}
</pre>
