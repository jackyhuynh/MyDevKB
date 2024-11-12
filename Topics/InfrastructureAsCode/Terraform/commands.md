# Comammands

### Core Terraform Commands
1. **`terraform init`**:
   - Initializes a working directory containing Terraform configuration files.
   - Downloads the necessary provider plugins.

2. **`terraform plan`**:
   - Generates and shows an execution plan without making any changes.
   - Helps preview the changes Terraform will make to your infrastructure.

3. **`terraform apply`**:
   - Applies the changes required to reach the desired state of the configuration.
   - Prompts for confirmation before applying, unless `-auto-approve` is used.

4. **`terraform apply -auto-approve`**:
   - Automatically approves and applies the changes without prompting for confirmation.

5. **`terraform destroy`**:
   - Destroys the Terraform-managed infrastructure.
   - Prompts for confirmation before destroying, unless `-auto-approve` is used.

6. **`terraform destroy -auto-approve`**:
   - Automatically approves and destroys the infrastructure without confirmation.

7. **`terraform output`**:
   - Reads and outputs the values of outputs defined in the configuration.

8. **`terraform show`**:
   - Displays the current state or a saved plan file in a human-readable format.

9. **`terraform state`**:
   - Used to manage the Terraform state file.
   - Subcommands include `list`, `show`, `rm`, `mv`, and `pull`.

10. **`terraform fmt`**:
    - Formats the Terraform configuration files to a standard format.

11. **`terraform validate`**:
    - Validates the configuration files for syntax and internal consistency without accessing any remote services.

12. **`terraform import`**:
    - Imports existing infrastructure into your Terraform state.

13. **`terraform refresh`**:
    - Updates the state file with the real infrastructure state.

14. **`terraform providers`**:
    - Displays the providers required by the configuration and their versions.

15. **`terraform taint`**:
    - Marks a resource for recreation during the next `apply`.

16. **`terraform untaint`**:
    - Removes the "tainted" state from a resource, indicating that it should not be destroyed and recreated on the next `apply`.

17. **`terraform workspace`**:
    - Manages workspaces, which allow you to create separate states for the same configuration.
    - Common subcommands include `new`, `list`, `select`, and `delete`.

18. **`terraform state list`**:
    - Lists resources in the current state.

19. **`terraform state show`**:
    - Shows the details of a resource in the current state.

20. **`terraform plan -out=<filename>`**:
    - Saves the plan to a file to be applied later with `terraform apply <filename>`.

21. **`terraform graph`**:
    - Generates a visual representation of the configuration and its resources.

22. **`terraform apply -var="variable_name=value"`**:
    - Overrides a variable value for the current apply run.

23. **`terraform apply -var-file=<filename>`**:
    - Loads variable definitions from a specific file.

### Best Practices
- **Always run `terraform plan`** before `terraform apply` to understand the changes that will be made.
- Use **`terraform fmt`** to keep your code clean and standardized.
- **Version control** your Terraform state file (`terraform.tfstate`) but be cautious with security-sensitive information.