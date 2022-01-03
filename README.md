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
male = 'Male'
female = 'Female'


Member -
================

data_members:
--------------
id - Integer
name - String
gender - Enum Gender
mother - Member
father - Member
spouse - Member
children - List <Member>

methods:
-----------------
constructor - params: Integer id, String name, String gender
set_mother - params: <Member> mother
set_father - params: <Member> father
set_spouse - params: <Member> spouse
add_child - params: <Member> child

get_paternal_grandmother - params: None
get_maternal_grandmother - params: None
get_spouse_mother - params: None

get_paternal_aunt - params: None -> self.father.mother.children.filter(female)
    - grandmother is None - []
    - grandmother is valid, but only one child, your father - []
    - grandmother is valid, multiple children, but no girls only boys - []
    - grandmother is valid, multiple children, girls and boys - [girls]

get_paternal_uncle - params: None -> self.father.mother.children.filter(male)
    - grandmother is None - []
    - grandmother is valid, but only one child, your father - []
    - grandmother is valid, multiple children, but all girls and our father - []
    - grandmother is valid, multiple children, both boys and girls - [boys, father is not included]

get_maternal_aunt - params: None -> self.mother.mother.children.filter(female)
get_maternal_uncle - params: None -> self.mother.mother.children.filter(male)

get_brother_in_law - params: None -> self.spouse.mother.children.filter(male)
    - spouse mother is None - []
    - spouse mother is valid, but only one child, our spouse - []
    - spouse mother is valid, multiple children, all girls and our spouse- []
    - spouse mother is valid, multiple children, boys and girls - []

get_sister_in_law - params: None -> self.spouse.mother.children.filter(female)
get_son - params: None
get_daughter - params: None
get_siblings - params: None



