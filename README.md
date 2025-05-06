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
  ### IdentityRole : 
   - Represents a role in the system (e.g., Admin, User, Moderator).
  ### UserManager<TUser> : 
   - A service that provides high-level APIs to manage users of type TUser (typically IdentityUser or a derived class like ApplicationUser).
   - **Used for:**
      - Creating users
      - Validating passwords
      - Adding users to roles
      - Managing user claims, tokens, lockouts, etc.
    - **Example:**
        ```
        var result = await _userManager.CreateAsync(user, "Password123!");
           await _userManager.AddToRoleAsync(user, "Admin");
        ```

  ### UserRole (usually IdentityUserRole<TKey>):
  - A join table that maps users to roles.
  - Used internally by Identity to connect IdentityUser and IdentityRole.
  - You typically don’t use this directly unless customizing the identity schema.


 
