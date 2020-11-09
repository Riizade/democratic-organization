# Constitution
This document outlines the structure of the organization. In the event that this document conflicts with rules, policies, procedures, or other documents of the organization, this document always takes precedence.

## Configuration Variables
Text in this document which resembles `$variable-name` represents a variable. The text should be replaced with the appropriate value specified in `configuration.yaml` before enforcing the rules of this document. Configuration in this way allows for this document to scale easily for organizations of different sizes and preferences.

# Definitions
- Member: An individual participant within the organization.
- Role: An elected position granting a particular member specific privileges not afforded to other members within the organization.
- Proposition: A single issue on which members vote for the outcome.
- Proposition Batch: A batch of propositions for which voting begins and ends on a pre-specified date.
- Option: A single choice on a proposition for which members can vote.

# Voting
Voting takes place via a webservice where aggregate tallies are publicly displayed. All votes are private to discourage social pressures from interfering with genuine expression of a member's desires. Voting is tied to an individual member's identity via a public/private key pair. A member is able to change their vote at any time up until the vote has been closed. At any time whether before vote closure or after vote closure, a member is able to check the vote that has been submitted using their identity by proving they have access to their private key.

## Petitions
Petitions are used to create propositions. A petition has two parts: the entire specification of the proposition that will be created, and the designated proposition batch cadence which will include the proposition if the proposition passes. Petitions collect signatures using each member's cryptographic key pair. Petition creators and signatories are kept private. A petition moves forward and is included in the next proposition batch of the specified cadence if it reaches a minimum of `$petition-required-signatures` signatures. A member can create a petition at any time and create as many petitions as they wish. Petitions can exist indefinitely. Members can remove their signature from a petition at any time.

### Constitution Petition
A petition which specifies a proposition that changes this document must reach at least `$constitution-petition-required-signatures` before the proposition will be included in the next batch. The proposition additionally may only be included in a proposition batch lasting for 25 days or longer.

### No Confidence Petition
No confidence petitions are special case petitions that do not become propositions. A no confidence petition simply specifies the name of a role. In the event that a no confidence petition reaches `$petition-required-signatures`, all members assigned to the specified role are immediately stripped of their privileges and the assigned Backup Officer(s) assume the role.

## Propositions
Propositions can change anything about the structure, composition, configuration, or specification of organizational entity within the company. Propositions include, but are not limited to:
- Changes to the constitution
- Changes to the organization variable configurations
- Changes to the assignment of a role

Propositions have 3 key components:
- The text of the proposition describing what is being proposed
- A list of choices for the outcome
- The type of voting used to decide the outcome

### Options
When created, propositions are not required to provide any options for the outcome. However, at any time until the vote closure (even during the petition stage and before the proposition batch opens for voting) any member can add any number of additional options.

### Voting Types
When creating a proposition (usually via a petition), the creator must choose exactly one of the voting methods outlined below.

#### Multiple Choice
Each member can select as many options as they like. The option with the most selections upon vote closure wins.

#### Ranked Choice
Each member orders the options according to their preferences. The winning option is chosen via instant runoff.

#### Weighted Vote
Each member gains a specified number of votes. The number specified must be the same for all members. Each member can apportion their allotted votes however they wish among any number of options. The option with the most votes wins.

## Proposition Batches
There are a number of proposition batch cadences. There is only one proposition batch open for each cadence at any given time. Proposition batches have a start date and an end date.

### Batch Cadences
#### Weekly Batch
Weekly batches begin and end at 12:00AM `$timezone` on Friday each week

#### Monthly Batch
Monthly batches begin at 12:00AM `$timezone` on the first day of each month and end at 11:59PM `$timezone` on the final day of the same month.

### Batch Lifecycle
#### Before Start Date
- Successful petitions have their propositions added to the batch
- Options can be added to propositions in the batch

#### Between Start and End Dates
- Options can be added to propositions in the batch
- Members can make selections as part of the voting process
- Members can change their vote selections
- Members can view their vote selections

#### After End Date
- Members can view their vote selections

# Roles
Roles are elected positions within the organization. Roles and members have a many-to-many relationship. That is, multiple members can hold a role simultaneously unless otherwise specified, and a member may hold multiple roles simultaneously unless otherwise specified.

## Candidacy
Any member is able to hold any role (and any number of roles) without restriction as long as they win the election process for that role.

## List of Roles

### Member Committee
This role must be occupied by at least `$member-committee-minimum` people at all times.

If at least `$fire-threshold` (rounded up) of those in the role agree, this role can eject any member from the organization for any reason at any time.

If at least `$hire-threshold` (rounded up) of those in the role agree, this role can allow any person outside the organization to join as a member at any time.

### Voting Officer
Has access to the machines and service which control voting. The voting officer ensures the integrity of the voting process.
The Voting Officer has the following privileges:
- Can access the underlying data of the voting service
- Can alter operation of the voting service to fix bugs or combat malfeasance
- Can check the option selection of each member and the overall tallies (to ensure that there is no discrepancy between the displayed options and the options used for tallying in the event of a bug or malicious activity)

### Backup Officer
In the event that a no confidence petition passes, the Backup Officer temporarily assumes that role until a new role assignment can be chosen.

## Elections
Elections take place twice yearly, on March 1st and September 1st of each year. On each of these dates, a new proposition is automatically added to the monthly issue batch beginning on those dates.