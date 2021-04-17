# Sending-E-Mail-from-Python
This repository contains function for sending plain text mails from Python. The reference is https://realpython.com/python-send-email/ .
Please refer this link on a more thorough study on this topic.

Its a small piece of code snippet. Do copy it where ever applicable.

```
# Create a function that takes in sender's email, receiver's email and message sends the message accordingly
def mail_signal(sender_mail, recipient_list, message):
    smtp_server = "smtp.gmail.com"
    port = 587  # For starttls
    password = open("PWD","r").read() #input("Type your password and press enter: ")

    # Create a secure SSL context
    context = ssl.create_default_context()

    # Try to log in to server and send email
    try:
        server = smtplib.SMTP(smtp_server,port)
        server.ehlo() # Can be omitted
        server.starttls(context=context) # Secure the connection
        server.ehlo() # Can be omitted
        server.login(sender_email, password)
        server.sendmail(sender_mail, recipient_list, message)# TODO: Send email here
    except Exception as e:
        # Print any error messages to stdout
        print(e)
    finally:
        server.quit() 
```
