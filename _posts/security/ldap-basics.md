# [1]

## Chapter 1

- A directory is an ordered listing of information about objects.

- Directories are designated to store relatively static information (i.e., information that rarely changes) and are optimized for read accesses.

- Directories are not required to support transactions.

- Communication with directories is usually done via client-server models.

  ![ldap-client-server-interaction]({{ site.url }}/assets/imgs/ldap/client-server-interaction.png)

- LDAP is designed as a light-weight alternative to DAP used by the X.500 standard. Basically, it defines the communication protocol between directory clients and servers.

- Two kinds of LDAP servers
  - Gateway servers which act as the bridges between LDAP clients and X.500 servers which provide accesses to the directories.
  - Standalone servers which directly access the directories.

## Chapter 2

- LDAP defines the content of the messages exchanged between the clients and servers. The messages can specify operations requested by the clients, or the responses from the servers.

- LDAP uses the X.500 directory model. It organizes data into _entries_ each of which represents an object.

- Each entry has a distinguished name (DN) which uniquely identifies it. Each DN contains a sequence of parts called relative distinguished names (RDN). The entries are arranged into a tree-like structure by their DNs. The tree-like structure is also called the directory information tree (DIT).

- An entry can have _attributes_ to describe it, and each attribute has a value and a type.

- A _schema_ defines what object classes are allowed where in the directory, what attributes they must contain, what attributes are optional, and the syntax of each attribute.

### LDAP models

- Information models
  - Define the general information structure

    ![entries-attributes]({{ site.url }}/assets/imgs/ldap/entries-attributes.png)

  - The type of an attribute is specified by a syntax. Some example syntaxes are cis, ces, tel, dn. A syntax defines what kind of values an attribute can have.
  - Inheritance between object classes are supported.
  - There is one special object class, `top`, which is the superclass of all other classes.
  - Each directory entry includes the mandatory attribute `objectClass`. This attribute consists of a list of schema names, which define the types of the objects that the entry represent.

- Naming models
  - Define how entries are identified and organized.
  - Entries are organized in DIT and arranged by their DNs.

    ![DIT-example]({{ site.url }}/assets/imgs/ldap/DIT-example.png)

    In the picture, each box is a directory entry.

  - An entry's DN is formed in the direction from the entry to the directory root.
  - The names of an entry's attributes are case insensitive.
  - DIT can be distributed among multiple servers. The highest entry stored by a server is called suffix. A server also stores referrals used to point to the DITs in other servers. A referral is an entry which is of `objectClass` referral and has an attribute `ref` whose value is the LDAP url to the referred entry in the other LDAP server.

    ![referrals]({{ site.url }}/assets/imgs/ldap/referrals.png)

- Functional models
  - Define the operations to access or modify directory entries.
  - Three main types
    - Query
    - Update
    - Authentication

- Security models
  - Define how to authenticate and authorize LDAP clients

- Authentication methods
  - No Authentication
  - Basic Authentication
  - Simple authentication and security layer (SASL)

- LDAP Data Interchange Format (LDIF)
  - An LDIF consists of a sequence of records separated by line separators. Each record consists of a sequence of lines and is used to describe an entry or an update to the directory.
  - An LDIF file can be used to describe either the directory entries or the updates to the directory but not both.

## Chapter 3

# [2]

## Chapter 2

- The left-most component of a DN is called RDN.


# Reference

[1] Understanding LDAP, IBM Redbook
[2] Understanding and Deploying LDAP Directory Services, Second Edition
