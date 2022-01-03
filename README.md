# geektrust-meetfamily
Geektrust problem for Backend 

#### PROBLEM STATEMENT #####

https://www.geektrust.in/coding-problem/backend/family

Application is designed to utilize TEST-DRIVEN-DEVELOPMENT approach

python -m unittest discover -s "./tests/unit/" -p "test_*.py"

CHILD ADDITION:
1. Cannot have duplicate names -> CHILD_ADDITION_FAILED
2. If tree is empty add -> CHILD_ADDITION_SUCCEEDED
3. Cannot be added through father -> CHILD_ADDITION_FAILED
4. Both father and mother need to exist -> PERSON_NOT_FOUND
5. All cases successful -> CHILD_ADDITION_SUCCEEDED

SPOUSE ADDITION:
1. Cannot have duplicate name -> SPOUSE_ADDITION_FAILED
2. Cannot be added if tree is empty -> SPOUSE_ADDITION_FAILED
3. Spouse needs to exist -> PERSON_NOT_FOUND
4. Spouse gender needs to be opposite -> SPOUSE_ADDITION_FAILED
5. Spouse cannot have an existing spouse -> SPOUSE_ADDITION_FAILED

GET_RELATIONSHIP NOTE:
The names of people in the relationship need to be printed in order of their addition.
1. Person should exist -> PERSON_NOT_FOUND
2. Should return non empty list -> NONE


Gender - 
===============

data_members:
-------------

male = 'Male' </br>
female = 'Female' </br>



Member -
================

data_members:
--------------

id - Integer </br>
name - String </br>
gender - Enum Gender </br>
mother - Member. </br>
father - Member. </br>
spouse - Member. </br>
children - List <Member> </br>

methods:
-----------------
constructor - params: Integer id, String name, String gender  </br>
set_mother - params: <Member> mother </br>
set_father - params: <Member> father </br>
set_spouse - params: <Member> spouse </br>
add_child - params: <Member> child </br>

get_paternal_grandmother - params: None. </br>
get_maternal_grandmother - params: None. </br>
get_spouse_mother - params: None. </br>

get_paternal_aunt - params: None -> self.father.mother.children.filter(female) </br>
    - grandmother is None - []. </br>
    - grandmother is valid, but only one child, your father - []. </br>
    - grandmother is valid, multiple children, but no girls only boys - [] </br>
    - grandmother is valid, multiple children, girls and boys - [girls]. </br>

get_paternal_uncle - params: None -> self.father.mother.children.filter(male). </br>
    - grandmother is None - []. </br>
    - grandmother is valid, but only one child, your father - []. </br>
    - grandmother is valid, multiple children, but all girls and our father - [] </br>
    - grandmother is valid, multiple children, both boys and girls - [boys, father is not included]. </br>

get_maternal_aunt - params: None -> self.mother.mother.children.filter(female).  </br>
get_maternal_uncle - params: None -> self.mother.mother.children.filter(male). </br>

get_brother_in_law - params: None -> self.spouse.mother.children.filter(male).  </br>
    - spouse mother is None - []. </br>
    - spouse mother is valid, but only one child, our spouse - []. </br>
    - spouse mother is valid, multiple children, all girls and our spouse- []. </br>
    - spouse mother is valid, multiple children, boys and girls - []. </br>

get_sister_in_law - params: None -> self.spouse.mother.children.filter(female). </br>
get_son - params: None. </br>
get_daughter - params: None. </br>
get_siblings - params: None  </br>



