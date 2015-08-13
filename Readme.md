WorldState
==========

What is this
----------------

WorldState is an object that is designed to handle multiple states as well as checking if all of the states are within specific constraints, by comparing them to a second WorldState.

Atoms
--------
 Each individual state within the WorldState, is called an atom inside the code. Each atom can only have a value between 0 and 255. Atoms have their own op code which declares what will happen to the atom when two WorldStates are added. Atoms also each have a dont care bit that will prevent them from functions like WorldState addition from affecting them.

Comparing WorldStates
-------------------------------
Each atom has an opcode that can either be used be a comparator like WSOP_EQUAL, or an op code that has a side effect like WSOP_ADD. To check if one WorldState satisfies constraints, use the function WorldStateTruth with the first WorldState being the WorldState to be checked and the second WorldState containing the constraints. The first WorldState's op codes will not be used while the second WorldState should use comparator values for their op codes.

Adding WorldStates
--------------------------
WorldStates have two ways to be added to. The first way is to use WorldStateAdd, where the values from the WorldState _From are added to the WorldState _To only if _To's DontCare variable for that atom is set to 0. The other way is to use the function WorldStateAddAtom which will add the the parameter _Value to the desired atom. WorldStateAddAtom will also set the DontCare variable for the atom to 0 if it is not already.
