PA2 Reflection

TODO 1: This makes the choices array based on how many choices the scene has and sets them to nullptr. It is O(1) because there can only be 3 choices.

TODO 2: This deletes all the child scenes, the choices array, and the data. It is O(n) because deleting the root ends up deleting every scene.

TODO 3: Checks if the scene has 0 choices which means its an ending. O(1).

TODO 4: Gets a choice at an index and returns nullptr if the index is bad. O(1).

TODO 5: Puts a scene into a choice spot if the index is valid. O(1).

TODO 6: Recursively goes through the tree and counts all the scenes. O(n) because it has to visit every scene.

TODO 7: Basically the same thing but only counts scenes that are endings. O(n).

TODO 8: Finds the longest path to an ending recursively. It checks the heights of the children and takes the biggest one. O(n).

TODO 9: Deletes the root and sets it to nullptr. The Scene destructor handles deleting everything else. O(n).

TODO 10: Opens the file, gets the starting HP and then loads the story. O(n) because the whole story has to be loaded.

TODO 11: Reads a scene and then recursively reads all the scenes below it. It also checks that there arent more than 3 choices. O(n).

TODO 12: Keeps asking until the user actually enters a valid choice. Each check is basically O(1), but the user can keep entering wrong stuff forever.

TODO 13: Plays through the story and changes HP, loot, and inventory as you go. Worst case is O(n) for going through the story, plus inventory searches.

TODO 14: Prints the amount of scenes, endings, and the height. The functions it calls go through the tree so its O(n).

TODO 15: Starts printing all the endings by calling printEndings. O(n).

TODO 16: Recursively goes through the story and prints every ending and the path to get there. O(n).

TODO 17: Greedy just picks whatever next choice has the most loot and keeps going until it dies or ends. Worst case O(n).

TODO 18: This recursively checks all the possible choices and figures out which surviving path gives the most loot. O(n) because even though it checks every path, each scene in the tree only gets visited once.

TODO 19: Calls bestLoot and prints the best path it found. O(n).

2. Exact Size Allocation

I used exactly numChoices slots because theres no point making 3 slots for every scene if they arent being used. If its an ending then choices is just nullptr because it has no choices.

3. Destructor

The destructor deletes the child scenes first. Then it deletes the choices array and data. Deleting a child also deletes all of its children so eventually the whole tree gets deleted.

If I deleted the choices array first then I would lose the pointers to all the child scenes and wouldnt be able to delete them anymore. That would cause memory leaks.

4. Greedy vs Optimal

My story is about being stuck on a broken spaceship. I made the cargo room have a lot of loot at the start so greedy would want to go there.

Greedy takes path 1-1-1.

It goes for the cargo room and alien crystals because they have a lot of loot, but then it ends up dying in the reactor.

Optimal takes the safer bridge route 2-1-1-1-1-1.

It doesnt get as much loot right away but it stays alive and gets more stuff later from the probe and supply station and eventually gets back to Earth.

Basically greedy loses because it only cares about what looks best right now while optimal actually checks what happens later.

5. Why bestLoot is O(n)

Even though bestLoot checks every path, its still O(n) because this is a tree. Every scene only has one parent so the same scene isnt getting checked over and over from different paths. Each scene basically gets visited once.

6. List Methods

I use search to check if an item is already in the inventory. I use addFront to add new items. I use size to show how many items the player has and print to show the inventory at the end.

Search can be O(b) where b is the amount of items in the bag because it might have to go through the whole linked list to find something.