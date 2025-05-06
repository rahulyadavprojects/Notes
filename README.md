# ASP.Net Core

## UserManager, UserRole, IdentityUser, IdentityRole --> Difference
###  IdentityUser : 
  - A built-in class in ASP.NET Core Identity that represents a user in your application.
  - **Custom User Mode** : You can extend IdentityUser with your own fields by creating a class like:
    ```
       public class ApplicationUser : IdentityUser
        {
            public string FullName { get; set; }
        }
    
    ```
 
