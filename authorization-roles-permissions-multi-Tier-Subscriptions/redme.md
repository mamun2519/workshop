# Authentication vs Authorization

**Authentication:** Authentication is the process of verifying the identity of a user or entity. It confirms that the person or system is who they claim to be. Ex. Entering a username and password to log into a website.

**Authorization:** Authorization is the process of determining whether an authenticated user has the right to access specific resources or perform certain actions. Ex. Once logged in, being able to access specific sections of a website based on user roles, like admin or regular user.

**Key Differences:**

**Authentication**

- Authentication focuses on verifying identity
- Authentication occurs at the beginning
- Authentication is about “who you are”
- Error Status Code:

**Authorization**

- Authorization focuses on granting or denying access
- To be authorized users must be authenticated
- Authorization is about “What you can do”
- 401 Error Status Code: 403
  Real-World Examples and Analogies

Hotel Check in:

Authentication: When you check into a hotel, you present your ID and booking confirmation. The hotel verifies your identity and reservation.
Authorization: Once checked in, you receive a room key that grants you access to your specific room, gym, pool, and other amenities based on your booking.
Concert Tickets:

Authentication: At the concert entrance, you show your ticket to verify you have the right to enter the event.
Authorization: Your ticket might also specify your seat, access to VIP areas, or backstage passes, determining what parts of the venue you can access.
Library Membership:

Authentication: To enter the library, you present your library card, which confirms your membership.
Authorization: With the library card, you can borrow certain types of books, access study rooms, or use special collections based on your membership level.
The Role of Authorization in Modern Applications
Authorization is a critical component of modern applications, ensuring that users can only access the data, features, or services they are permitted to use. Poor authorization can lead to security breaches, compliance failures, and a degraded user experience.

Security Benefits
Prevents Unauthorized Access – Ensures only permitted users can access sensitive resources.
Minimizes Attack Surface – Restricts permissions, reducing potential exploits.
Protects Data Integrity – Prevents unauthorized modifications to critical data.
Mitigates Insider Threats – Employees have access only to what's necessary (principle of least privilege).
User Experience Benefits
Personalized Access – Users see only relevant features and data.
Frictionless Navigation – No unnecessary access requests or confusion.
Seamless Subscription Upgrades – Automatically unlocks premium features.
Reduce Mistakes - Reduce the chance of mistakes happen by unwilling actions.
Partial Rollouts - Enable new features to the certain group of users
Common Authorization Failures & Real-World Cases
Broken Access Control: Users can perform actions they shouldn't have access to. Example: A guest user in a social medial app modifies other users posts. GitHub (2012): A broken authorization flaw allowed unauthorized users to modify repositories.
Insecure Direct Object References: Attackers access unauthorized data by modifying URLs or request parameters. Example: A user changes /user/123/profile to /user/124/profile and sees another user's data. Facebook Bug Bounty (2019): IDOR in Facebook allowed users to delete anyone's Instagram photo.
Privilege Escalation: Users exploit vulnerabilities to gain higher access levels. Example: A customer support agent gains admin privileges by manipulating API requests. Uber Breach (2022): Hackers gained admin access by compromising a contractor's credentials.
Regulatory & Compliance Considerations: Key Regulations
GDPR (EU) – Protects user data privacy.
General Data Protection Regulation: https://gdpr-info.eu/
HIPAA (US) – Ensures healthcare data security: https://www.hhs.gov/hipaa/for-professionals/privacy/laws-regulations/combined-regulation-text/index.html
Health Insurance Portability and Accountability Act
SOC 2 – Enforces strong access control in SaaS.
Systems and Organization Controls 2: https://secureframe.com/hub/soc-2/compliance-documentation
PCI DSS – Secures payment processing.
Payment Card Industry Data Security Standards: https://www.pcisecuritystandards.org/standards/
Examples:

A messaging app must ensure that only users can read their own messages. Even employees or admins should not have access to private chats. This prevents unauthorized access and protects user privacy. (GDPR)
In a hospital system, only doctors should access patient records. Receptionists can see appointment details but not medical history or test results. This ensures patient data remains confidential. (HIPAA)
A sales team using a CRM system should have restricted access to leads. Sales representatives should only see their own clients and not their colleagues’ deals to prevent data leaks. (SOC 2)
In HR software, only senior HR personnel should be able to see salary details. Regular employees or interns must not have access to prevent privacy violations. (GDPR)
An online therapy platform must ensure that only assigned therapists can access patient notes. Other employees or therapists should not see confidential data. (HIPAA)
A restaurant's payment system must only show the last four digits of a credit card number. Full card details should never be visible to waiters to prevent fraud. (PCI DSS)
Software engineers working on a banking app should not have access to customer account balances. They should only work with test data, ensuring security. (SOC 2)
A healthcare messaging app must ensure that only doctors and patients can see their conversations. Support agents should not have access to medical discussions. (GDPR + HIPAA)
Detailed Overview of Authorization Techniques
Role-Based Access Control (RBAC)
RBAC assigns permissions based on predefined roles (e.g., Admin, Editor, Viewer). Users are assigned roles, and each role has a specific set of permissions. This is the most basic authorization techniques and no dynamic permissions.

Example: In an HR system, an HR Manager can access all employee records, while a regular employee can only view their own data.

Permission-Based Access Control (PBAC)
PBAC assigns explicit permissions to users or roles. Permissions are checked before granting access.

Examples: A project management tool where:

Admins can create, edit, and delete projects.
Managers can create and edit but not delete projects.
Employees can only view projects.
https://drive.google.com/file/d/1bJ82DBU46lYkfKSX5WfsWFfwhgM0vkvr/view?usp=sharing

Attribute-Based Access Control (ABAC)
ABAC defines access rules based on attributes (user attributes, resource attributes, and environment conditions). Instead of fixed roles, it evaluates conditions dynamically.

Use Cases: Fine-grained access control in SaaS, healthcare, and financial apps.

Example: A banking app allows transactions only if:

The user’s risk score is low.
The device is trusted.
The transaction amount is below $10,000.
https://drive.google.com/file/d/1C7iin8ofnpGVCOxQTiqViZBBdF2Geqpl/view?usp=sharing

Policy-Based Access Control (PBAC)
PBAC extends ABAC by using policies to define access rules. Policies are centralized and can be updated without modifying code. Example: A cloud storage service allows access only if:

The user’s role is "employee".
The user’s IP address is from an approved country.
The user is accessing during business hours (9 AM - 5 PM UTC).
https://drive.google.com/file/d/1y2Gt_7bhyc5SMV-c7jHTLs-hSFnLrKsb/view?usp=sharing

Discretionary Access Control (DAC)
DAC allows the resource owner to decide who can access their resources. It is commonly used in file-sharing and collaboration tools. Example: Google Drive / Dropbox style file sharing

A user (owner) can decide who has access to a document.
Users can be granted view or edit permissions.
The owner can revoke access at any time.
https://drive.google.com/file/d/1q_dSZ2LyN3lK04SluSgxGo4AjnUeRfau/view?usp=sharing

Mandatory Access Control (MAC)
MAC is strict and non-discretionary. It enforces predefined security policies where users cannot modify access controls. Typically used in government and military systems.

Use Cases: Military, classified data protection, financial institutions.

Example: A defense system ensures that only personnel with ‘Top Secret’ clearance can access classified reports.

Just-In-Time (JIT) Access Control
JIT access grants temporary permissions only when needed and revokes them after use.

Use Case: DevOps, cloud infrastructure, high-security environments.

Example: A developer requests admin access to a production server for debugging. After 30 minutes, access is automatically revoked.

Feature-Based Access Control (FBAC)
FBAC restricts access based on feature flags instead of user roles.

Use Case: SaaS applications, subscription-based models.

Example: A free-tier user can access basic features, while a premium user unlocks advanced analytics.

https://drive.google.com/file/d/1XWZoQUJGPLP2V9wQ2A0Js0FcusNl7BTM/view?usp=sharing

Hierarchical Access Control
Hierarchical systems allow inheritance of permissions across different levels.

Use Case: Multi-tiered organizations, government agencies.

Example: A CEO can access all company documents, while managers can only see reports relevant to their department.

https://drive.google.com/file/d/1hDMYAWMjD390hKxpzzolHXhHgelB9ACN/view?usp=sharing

Understand Role Hierarchy & It’s Importance
In complex applications like SaaS, implementing a role hierarchy is crucial for managing access control efficiently. Role hierarchy allows organizations to structure roles in a way that reflects their operational needs, enabling fine-grained access control.

Role Hierarchy
Role hierarchy organizes roles in a parent-child relationship, where higher-level roles inherit permissions from lower-level roles. This structure simplifies permission management and ensures that users at different levels have appropriate access.

Key Concepts:
Parent Roles: Higher-level roles that grant broader permissions.
Child Roles: Lower-level roles that inherit permissions from parent roles but can also have additional restrictions.
Inheritance: Lower-level roles automatically gain permissions from their parent roles, reducing redundancy in permission assignments.
Example of Role Hierarchy:
CEO: Has access to all company documents and settings.
Manager: Inherits access to view reports but can also manage team-specific documents.
Employee: Can view specific documents relevant to their tasks.
Corporate Structure:

Administrator: Full access to all features and settings.
HR Manager: Can manage employee records and reports.
HR Employee: Can view and update employee information.
Educational Institution:

Principal: Access to all school data and reports.
Teacher: Can access class schedules and student records.
Student: Can view personal grades and assignments.
E-commerce Platform:

Owner: Full control over the platform and product management.
Admin: Manages inventory and orders.
Staff: Can assist with customer inquiries and order processing.
https://drive.google.com/file/d/197mUtR5v3PoBwUqSBnfkm7y2hm1E4st2/view?usp=sharing

Benefits of Role Hierarchy
Simplified Management: Reduces complexity by allowing permissions to be set at higher levels, automatically applying them to all child roles.
Scalability: Easily accommodates changes in the organization structure by adding or modifying roles without disrupting existing permissions.
Consistency: Ensures that users with similar responsibilities have consistent access, reducing the likelihood of misconfigurations.
Fine-Grained Control: Allows organizations to define specific permissions for different levels, ensuring that sensitive data is accessible only to those who need it.
Challenges of Role Hierarchy
Risk of Over-Permissioning: If not carefully managed, users at lower levels may inherit more permissions than intended, leading to security risks.
Complexity in Maintenance: As the organization grows, maintaining and updating the role hierarchy can become complex and time-consuming.
Conflict Resolution: Conflicts may arise when different roles have overlapping permissions, necessitating clear policies to manage these situations.
Potential for Confusion: Users may be unclear about their actual permissions, especially if the hierarchy is deep or poorly documented.
Managing Subscriptions using Roles and Permissions
In many SaaS applications, managing user subscriptions through roles is a common and effective approach. Each subscription level can be associated with specific roles that determine what features or data the user can access.

Defining Roles for Different Subscription Levels
For instance, in a SaaS application with multiple subscription tiers, you might define roles like:

Free Tier: Basic access to limited features.
Pro Tier: Access to advanced features and additional data.
Enterprise Tier: Full access to all features, plus premium support.
Strategies for Managing and Updating Roles Dynamically
To manage roles effectively, you can implement the following strategies:

Role Assignment on Subscription Purchase: When a user subscribes to a particular tier, automatically assign the corresponding role.
Role Upgrades: If a user upgrades their subscription, dynamically change their role to reflect the new tier.
Expiration Handling: If a subscription expires, revoke the role or downgrade to a lower tier automatically.
https://drive.google.com/file/d/1mlTN9xZ6KWoLJgqbJ9tf0p--7i6hLYDt/view?usp=sharing
