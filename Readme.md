# How can start? 
## Basic sctruture Model C4

```
workspace {

    model {
        user = person "User" #I
        softwareSystem = softwareSystem "Software System" #II

        user -> softwareSystem "Uses" #III
    }

    views {
        systemContext softwareSystem "Diagram1"  {         #IV
            include * 
            autoLayout #V
        }

        theme default #VI
    }

}
```
### Example render bellow => autolayout TB and LR

TB           |  LR
:-------------------------:|:-------------------------:
![Screen Shot 2022-06-23 at 22 26 50](https://user-images.githubusercontent.com/36551379/175441430-0ffcde2c-eb62-4f5f-b5a3-c3395e5beabf.png)| ![Screen Shot 2022-06-23 at 22 28 32](https://user-images.githubusercontent.com/36551379/175441607-b359f46f-8d39-4050-93b5-2d6d806c505b.png)




### EXTRA DETAIL -> Basic sctruture
######  I   | User => Who is to use the system. You can put something like these: Custumers, Financial Users, Manegers, Stackhoulders
###### II  | SoftwareSystem => Is your main, usually can have only one, is a big module that you have need zoom-in example: Payments, Account, Checkout
###### III | Interaction, when you need put an event: touchs, connection, spreeds. element A touch on element B in this case above ⬆️  we have user connect on > softwareSystem and we put a subtitle *Users, this subtitle is a small describe about event
###### IV  |  Here we customize your container, first params is your a context, the second params is the name the container that you cna customize, we're using > *softwareSystem because it's your name declaration in line 9 => softwareSystem = softwareSystem "Software System"
###### V   | Autolayout is the direction that your diagrams should be follow example: lr | Left to Right  or TB | Top to Bottom
###### VI  | We can choose your theme and customize the layout, the default theme is C4 Model Architecture

### Zoom-in

>Notes: You can create micro-environments  and use this micro-environments for interactions.

```
 internetBankingSystem = softwaresystem "Internet Banking System" "Allows customers to view information about their bank accounts, and make payments." {
     singlePageApplication = container "Single-Page Application" "Provides all of the Internet banking functionality to customers via their web browser." "JavaScript and Angular" "Web Browser"
     
     mobileApp = container "Mobile App" "Provides a limited subset of the Internet banking functionality to customers via their mobile device." "Xamarin" "Mobile App"
     
     webApplication = container "Web Application" "Delivers the static content and the Internet banking single page application." "Java and Spring MVC"
     
     apiApplication = container "API Application" "Provides Internet banking functionality via a JSON/HTTPS API." "Java and Spring MVC" 
            {
                    signinController = component "Sign In Controller" "Allows users to sign in to the Internet Banking System." "Spring MVC Rest Controller"
                     accountsSummaryController = component "Accounts Summary Controller" "Provides customers with a summary of their bank accounts." "Spring MVC Rest Controller"
                     
                     resetPasswordController = component "Reset Password Controller" "Allows users to reset their passwords with a single use URL." "Spring MVC Rest Controller"
                     
                     securityComponent = component "Security Component" "Provides functionality related to signing in, changing passwords, etc." "Spring Bean"
                     mainframeBankingSystemFacade = component "Mainframe Banking System Facade" "A facade onto the mainframe banking system." "Spring Bean"
                     emailComponent = component "E-mail Component" "Sends e-mails to users." "Spring Bean"
            }
     database = container "Database" "Stores user registration information, hashed authentication credentials, access logs, etc." "Oracle Database Schema" "Database"
     
}      
```
![Screen Shot 2022-06-23 at 22 49 11](https://user-images.githubusercontent.com/36551379/175446104-0ff9d433-a4ec-45fb-825c-4fe59ded8d68.png)

## Zoom-in Detail
![zoom-in](https://user-images.githubusercontent.com/36551379/175448186-ca87cf6e-e1c5-49b3-88cc-c927e1644575.png)

> Notes: The line:  apiApplication = container "API Application"...   Contain more one zoom-in because this componente contain more componente inside itself.

> Detail the  apiApplication = container "API Application" 
![Screen Shot 2022-06-23 at 23 12 02](https://user-images.githubusercontent.com/36551379/175448434-519d7298-d357-402f-ad69-cc407beb844f.png)

