# ASP.Net Core

## UserManager, RoleManager, UserRole, IdentityUser, IdentityRole --> Difference
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
  ### UserManager'<TUser> : 
   - A service that provides high-level APIs to manage users of type TUser (typically IdentityUser or a derived class like ApplicationUser).
   - **Used for:**
      - Creating users
      - Validating passwords
      - Adding users to roles
      - Managing user claims, tokens, lockouts, etc.
  - **Common Methods:**
   - `CreateAsync(user, password)`   -->  Creates a new user with a password
   - `FindByNameAsync("username")`   -->  Finds a user by username
   - `CheckPasswordAsync(user, "password")`   --> Verifies a password against stored hash
   - `AddToRoleAsync(user, "role")`   -->  Assigns the user to a role
   - `RemoveFromRoleAsync(user, "role")	`  --> Removes the user from a role
   - `GetRolesAsync(user)	`  --> Retrieves the roles assigned to the user
   - `GenerateEmailConfirmationTokenAsync(user)`   -->  Creates a token for confirming the user's email
   - `IsEmailConfirmedAsync(user)`   -->  Checks if the email is confirmed
   - `ResetPasswordAsync(user, token, newPwd)`  --> Resets the user’s password using a token
            
    - **Example:**
        ```
        var result = await _userManager.CreateAsync(user, "Password123!");
           await _userManager.AddToRoleAsync(user, "Admin");
        ```
    

  ### UserRole (usually IdentityUserRole<TKey>):
  - A join table that maps users to roles.
  - Used internally by Identity to connect IdentityUser and IdentityRole.
  - You typically don’t use this directly unless customizing the identity schema.
  ### RoleManager<TRole> : 
   - A service class in ASP.NET Core Identity used to manage roles.
   - The generic type TRole is typically IdentityRole or a custom class derived from it.
   - **What it's used for:**
      - RoleManager provides methods to:
         - Create, update, delete roles
         - Check if a role exists
         - Find roles by name or ID
         - Add or remove role claims
   - **Common Methods:**
      - `CreateAsync(role)`    -->    Creates a new role
      - `DeleteAsync(role)`    -->    Deletes an existing role
      - `RoleExistsAsync("RoleName")`   --> Checks if a role exists
      - `FindByNameAsync("RoleName")`   --> Gets role by name
      - `AddClaimAsync(role, claim)`    --> Adds a claim to a role
      - `RemoveClaimAsync(role, claim)`   --> Removes a claim from a role


 
