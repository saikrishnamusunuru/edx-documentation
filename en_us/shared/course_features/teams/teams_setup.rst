.. _Teams Setup:

##########################################
Using Teams in Your Courses
##########################################

This section provides information about setting up teams in your courses.

.. contents::
  :local:
  :depth: 2

For information about managing teams in your courses, see the following topics.

* :ref:`Teams Discussions`
* :ref:`CA Learner Experience of Teams`


.. _CA_Teams_Overview:

*******************************
Teams Overview
*******************************

Using teams in your course is an effective way for learners to interact and
collaborate on small group projects or activities. You define the structure of
teams in your course by defining "team-sets", groups of teams based around a specific
topic or assignment. Each learner can belong to one team per team-set, so you can set
up a team-set where learners can join a team to discuss a certain course topic,
or set up a team-set where learners can join a team to work on a group assignment.

When a team is created, it is given an name and description to identify it. 
A primary communication language can optionally be specified
and a primary country that members identify with. Team characteristics might
serve as the basis for attracting new members, resulting in small groups of
learners with similar interests and goals who will work together on projects
or activities within the same topic area.

Teams are most effective when learners have a clear reason for joining a team,
and a clear outcome to achieve with fellow team members. For example, you
might create an assignment that consists of a group project or activity, 
and ask learners to join teams of their choice within a specific team-set to complete
the assignment. Team members can use discussions within the team to communicate
and collaborate on the assignment. If you want only to  provide a way for learners
to connect socially, consider using discussions within the course rather than teams.
For more information about using discussions, see :ref:`Running_discussions`.


.. _Enable and Configure Teams:

*******************************
Enable and Configure Teams
*******************************

To enable and configure teams in your course, modify the **Teams
Configuration** policy key on the **Advanced Settings** page so that the key
includes team-set names and the maximum team size.

.. note:: The **Teams** page in the LMS becomes available only after you have
   specified at least one team-set.

.. note::  EdX recommends that you do not delete team-sets once your course is
   running. If you delete a team-set from the **Teams Configuration** policy key,
   that team-set is no longer visible in the LMS, and learners will not be able to leave
   teams associated with the deleted team-set even though they will still appear in
   their “My Teams” tab. Please delete learners from teams before deleting the
   associated team-set from **Teams Configuration**.


#. In Studio, from the **Settings** menu, select **Advanced Settings**,
   then locate the **Teams Configuration** policy key.

   By default, you see a set of curly braces ({}). You define team-sets and the
   maximum team size inside this set of braces.

#. To specify the maximum team size for teams in your course, enter the
   ``max_team_size`` parameter in double quotation marks, followed by a colon,
   then a positive integer value representing the maximum number of team
   members allowed. For example, to set the maximum number of learners per
   team in your course to 5, your entry would look like this example.

   ``"max_team_size": 5``

   Max Team Size should 

#. To specify team-sets within which teams can be created, add entries under
   ``"team_sets"``. For each team-set, provide a description, name, and ID as shown
   in the example. You may also optionally provide a ``"type"`` for each team-set,
   which sets the visibility and access for teams. Different ``"type"`` values are
   explained in the next section.

   Make sure that you enclose all of the sets of team-set values within a set of
   square brackets, with a comma after the closing square bracket.

   .. note:: If you create more than one team-set, make sure that you add a comma
      after the closing curly brace of each team-set that has another team-set
      following it. The syntax that you use must match the example syntax
      exactly. Missing or incorrect indentation, curly braces, brackets, or
      punctuation marks cause errors.

   .. note:: For team-set IDs, you can use only alphanumeric characters and the
      underscore, hyphen, and period characters.


::

   {
    "team_sets": [
        {
            "name": "Sustainability in Corporations",
            "description": "Description for Sustainability in Corporations",
            "id": "Sustain_Corporations",
            "type": "open"
        },
        {
            "name": "Water Conservation Projects",
            "description": "Description for Water Conservation",
            "id": "Water_Conservation",
            "type": "private_managed"
        },
        {
            "name": "Sustainability Standards and Reporting",
            "description": "Description for Sustainability Standards",
            "id": "Standards_Reporting",
            "type": "public_managed"
        }
    ],
    "max_team_size": 5
   }


The team-sets you have created appear on the **Teams** page in the LMS when
learners browse teams by team-set. The **Teams** page is not visible until you
have created at least one team-set.


.. image:: ../../../../shared/images/Teams_TopicsView.png
  :width: 600
  :alt: Three team-sets on the Browse Teams page.

.. _Team-set Types:

******************
Team-set Types
******************

Each team-set has a 'type'. Setting a team-set's type allows you to control who can see, create, and join teams within
the team-set. The three team-set types are:

- open (default)
- private managed
- public managed

Open team-sets are the least restrictive. Learners can freely join, leave, and create teams within an open team-set.
All teams within an open team-set, as well as their membership information, are visible to anyone enrolled in the course.

Private and Public Managed team-sets are referred to together as instructor-managed. In instructor-managed team-sets,
users cannot create, join, or leave teams. The creation, deletion, and membership of teams in an instructor-managed
team-set is all controlled by course staff. Course staff can control team membership through the **Manage** tab on
the **Teams** page. (The **Manage** tab only appears when there is at least one instructor-managed team-set defined
for the course.)

The difference between Private and Public Managed team-sets is visibility. In a Public Managed team-set, while learners
cannot create teams or control which team they are a member of, they can see every team in the team-set and their
memberships. In a Private Managed team-set, on the other hand, a user can only see their own team. They cannot see that any other
team in the team-set exists. Additionally, if a learner isn't in a team in a certain private team-set, they can't
see that the private team-set exists.

If a team-set is specified in the Advanced Course Settings without a 'type', the team-set will default to Open.

Here is a table to quickly compare the differences between the different team-set types. The 'Teams Configuration Value' 
column contains the value that you should set "type" to in the Course Advanced Configuration.

================  ===========================  ==========================  =====================================  =============================
 Name              Teams Configuration Value    Learner can create teams    Learner can join/leave teams freely    Learner can see other teams
================  ===========================  ==========================  =====================================  =============================
Open               open                         True                        True                                   True
Public Managed     public_managed               False                       False                                  True
Private Managed    private_managed              False                       False                                  False
================  ===========================  ==========================  =====================================  =============================


.. _Create a Team:

******************
Create a Team
******************

Although learners in your course may be able create their own teams in open team-sets, you can seed open
team-sets with a few teams to give learners some ideas for their own teams.

Course team members who have the **Staff**, **Admin**, **Discussion Admin**,
or **Discussion Moderator** role can create new teams within team-sets.
**Community TAs** and learners in the course can also create teams, although
learners can create a new team only in open team-sets and only if they do not already
belong to a team in that team-set.

To create a team, follow these steps.

#. From the **Teams** page in the LMS, select **Browse**, then select the
   team-set in which you want to create a team.

#. At the bottom of the list of teams within the team-set, select the **create a
   new team in this team-set** link.

   .. image:: ../../../../shared/images/Teams_CreateNewTeamLink.png
     :width: 600
     :alt: The "create a new team in this team-set" link


3. On the **Create a New Team** page, add a name and description for the team.

   In the description, include details about the proposed project or activity
   to help learners to decide whether they want to join this team.

   .. image:: ../../../../shared/images/Teams_CreateNewTeamForm.png
     :width: 600
     :alt: Empty form with fields to be completed when you create a new team.

#. Optionally, add some characteristics for your team. You can specify a
   language that members would primarily use to communicate with each other,
   and a country that members would primarily identify with. Keep in mind that
   if your team details make the team membership seem too selective, learners
   might be discouraged from joining.

#. When you have finished entering details for the team, select **Create**.

   Your new team is added to the list of teams under your selected team-set.



.. _Search for a Team:

******************
Search for a Team
******************

Use the search field to find a team within a team-set.

.. note:: Partial words are not supported for searching teams.

To get a list of teams whose names, descriptions, or characteristics match
your search keywords, follow these steps.

#. From the **Teams** page in the LMS, select **Browse**, then select the
   team-set in which you want to find a team.

#. In the search field, enter one or more keywords to search for, then press
   **Enter** or select the search icon.

   Teams within the team-set that match your search are displayed.

To clear the existing search term, select the **X** next to the search field,
or select all the text within the field and enter text to replace it.


.. _Edit a Team:

******************
Edit a Team
******************

Course team members who have the **Staff**, **Admin**, **Discussion Admin**,
or **Discussion Moderator** role can edit any of a team's details, including
removing members from a team. **Community TAs** can also edit teams. For more
details about removing team members, see :ref:`Remove Learner from Team`.

To edit a team's details, follow these steps.

.. note:: Before making significant changes to a team, communicate with team
   members so that they are aware of the changes and their impacts.

#. In the LMS, select the **Teams** tab.
#. On the **Teams** page, select **Browse** to show all team-sets.
#. Select the arrow button for the team-set to show all teams in that team-set.
#. Locate the team that you want to edit. To find the team, you can search
   using keywords or sort teams by last activity or open slots.
#. Select **View** for the team that you want to edit.
#. Select **Edit Team**.
#. Make your changes, then select **Update**.
   The team's details are updated.


.. _Remove Learner from Team:

********************************
Remove a Learner from a Team
********************************

Course team members who have the **Staff**, **Admin**, **Discussion Admin**,
or **Discussion Moderator** role can remove members from a team. **Community
TAs** can also remove learners from a team. You might want to remove a learner
from a team and make the spot on the team available to other learners if, for
example, a learner joined a team but is not participating, or if a learner has
unenrolled from the course without leaving the team.

.. note:: Before making significant changes to a team, communicate with team
   members so that they are aware of the changes you will make, and their
   impacts.

To remove a learner from a team, follow these steps.

#. In the LMS, select the **Teams** tab.
#. On the **Teams** page, select **Browse** to show all team-sets.
#. Select the arrow button for the team-set to show all teams in that team-set.
#. Locate the team that you want to edit. To find the team, you can search
   using keywords or sort teams by last activity or open slots.
#. Select **View** for the team from which you want to remove a learner.
#. Select **Edit Team**.
#. On the **Instructor Tools** bar, select **Edit Membership**.

   .. image:: ../../../../shared/images/Teams_InstructorToolsEditMembers.png
     :width: 600
     :alt: The Edit Membership button on the "Instructor Tools" bar on the Edit Team page.

#. On the team's **Membership** page, select **Remove** next to the name of
   the learner who you want to remove from the team.
#. In the confirmation message, select **Remove**.


   The team member you removed no longer appears on the **Membership** page.

#. Repeat steps 8 and 9 to remove additional members.

   The team members you removed no longer appear on the **Membership** page,
   and the count of team members is updated wherever it appears on team pages.





.. _Delete a Team:

******************
Delete a Team
******************

Course team members who have the **Staff**, **Admin**, **Discussion Admin**,
or **Discussion Moderator** role can delete teams. **Community TAs** can also
delete teams. you might need to manage the teams in your course, including
deleting teams that remain empty or where members are experiencing abusive
situations.

When you delete a team, all learners are removed from the team membership.
Neither learners nor course team members can access discussions from deleted
teams.

.. note:: Deleting a team removes it permanently from the course, and cannot
   be undone.

To delete a team, follow these steps.

#. In the LMS, select the **Teams** tab.
#. On the **Teams** page, select **Browse** to show all team-sets.
#. Select the arrow button for the team-set to show all teams in that team-set.
#. Locate the team that you want to delete. To find the team, you can search
   using keywords or sort teams by last activity or open slots.
#. Select **View** for the team that you want to delete, then select **Edit
   Team**.
#. On the **Instructor Tools** bar, select **Delete Team**.

   .. image:: ../../../../shared/images/Teams_InstructorToolsDeleteTeam.png
     :width: 600
     :alt: The Edit Membership button on the "Instructor Tools" bar on the Edit Team page.

#. In the confirmation message, select **Delete**.

   You return to the team-set page, where you receive a confirmation that the
   team has been successfully deleted. The team no longer appears in the teams
   list within its team-set. Learners who were previously members of this team no
   longer belong to a team.
