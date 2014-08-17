Go Trello client
----------------
This [Go](http://golang.org/) package implements the [Trello](http://www.trello.com/) [API](http://trello.com/api).

Example
-------

```
package main

import (
	"fmt"
	"github.com/VojtechVitek/go-trello"
)

func main() {
	// New Trello Client
	trello, _ := trello.NewClient()

	// User @trello
	user, _ := trello.Member("trello")
	fmt.Println(user.FullName)

	// @trello Boards
	boards, _ := user.Boards()

	if len(boards) > 0 {
		board := boards[0]
		fmt.Printf("* %v (%v)\n", board.Name, board.ShortUrl)

		// @trello Board Lists
		lists, _ := board.Lists()
		for _, list := range lists {
			fmt.Println("   - ", list.Name)

			// @trello Board List Cards
			cards, _ := list.Cards()
			for _, card := range cards {
				fmt.Println("      + ", card.Name)
			}
		}
	}
```

prints

```
Trello
* How to Use Trello for Android (https://trello.com/b/9dnaRkNt)
   -  Getting Started
      +  Welcome to Trello! This is a card.
      +  Tap on a card to open it up.
      +  Color-coded labels can be used to classify cards.
      +  Create as many cards as you want. We've got an unlimited supply!
      +  Here is a picture of Taco, our Siberian Husky.
   -  Diving In
      +  Tap and hold this card to drag it to another list.
      +  Tap on the board name to view other sections.
      +  Make as many lists and boards as you need. We'll make more!
   -  Mastering Trello
      +  Finished with a card? Drag it to the top of the board to archive it.
      +  You can reorder lists too.
      +  Invite team members to collaborate on this board.
   -  More Info
      +  Want updates on new features?
      +  You can also view your boards on trello.com
```

Influenced by
-------------
- [fsouza/go-dockerclient](https://github.com/fsouza/go-dockerclient)
- [jeremytregunna/ruby-trello](https://github.com/jeremytregunna/ruby-trello)

License
-------
Go Trello client is licensed under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0).