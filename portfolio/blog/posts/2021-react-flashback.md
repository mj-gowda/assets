---
title: "Creating an Entertaining Memory Game with React"
subtitle: "Improve Your Concentration and  memory Skills with Flashback Frenzy "
date: "2021-11-13"
---
## My First React Game - Flashback Frenzy

Welcome to my blog where I'll take you through my journey of creating my very first React game - Flashback Frenzy. In this blog post, I'll share my experiences in building this memory game, the game's user interface and file structure, the importance of React's `useState` and `useEffect`, the game logic, and how i made it available as a Progressive Web App (PWA).

### To play the Game <a href="https://flashback-frenzy.vercel.app/" target="_blank">Flashback-Frenzy</a>

![game](/images/flashback.png)

## Game Introduction

- *Flashback Frenzy* is a memory game that challenges your mind and sharpens your memory.
- It features a 4x4 grid of cards, each card hiding a unique element. The goal is to tap on the grid elements to reveal the cards and find their matching pairs. However, there's a catch – you can only reveal two consecutive cards at a time. 
- The challenge lies in remembering the previously revealed cards and matching them efficiently.



## Game UI and File Structure

### UI Design

- For the game's user interface, I used plain CSS to design the main card and its elements. The UI is clean and intuitive, making it easy for players to navigate through the game.
- Learning how to style individual components was fun and very interactive.

### File Structure (Vite Create React App)

The project's file structure follows the Vite Create React App convention:

- **src** folder contains components, hooks, and utilities.
- **src/components** houses the main game logic components, including `Card.js` and `Header.jsx`.
- **public** contains all the images of the card elements.
- **utilities** folder holds `shuffle.js`, a utility function used to randomly shuffle the elements for a new game.

This organized structure helps keep the codebase clean and maintainable.
![game](/images/flashback-1.png)



### Basics of `useState` and `useEffect` Needed for This Project

- In order to understand and implement Flashback Frenzy, I needed to grasp the basics of `useState` for managing component state and `useEffect` for handling side effects such as fetching data, updating the DOM, or in our case, controlling game logic.

- For those who want to delve deeper into these React hooks, I recommend reading further about them <a href="/posts/2021-react-usestate">Here</a>


## Game Logic: Building the Brain Behind Flashback Frenzy

Now, let's delve into the heart of Flashback Frenzy – its game logic. The following sections will explain how the game functions and how I've implemented it in the code.

## Managing Game State

To create the game, I use React's state management features, `useState` and `useEffect`. These hooks are essential for keeping track of various aspects of the game:

```javascript
const [wins, setWins] = useState(0);       // Win streak
const [cards, setCards] = useState(shuffle);// Cards array from assets
const [pickOne, setPickOne] = useState(null);// First selection
const [pickTwo, setPickTwo] = useState(null);// Second selection
const [disabled, setDisabled] = useState(false);// Delay handler
const [setBadge, clearBadge] = useAppBadge();  // Handles app badge
```


### Handling Card Selection

The handleClick function manages card selection when a player taps on a card. It checks whether the player can make a selection based on the disabled state and assigns the selected card to either pickOne or pickTwo:

```javascript
const handleClick = (card) => {
  if (!disabled) {
    pickOne ? setPickTwo(card) : setPickOne(card);
  }
};
```

### Managing Turns and Starting a New Game

The handleTurn function resets the game state, allowing the player to make new selections. It's called after a pair of cards is matched or when a delay between selections is needed:

```javascript
const handleTurn = () => {
  setPickOne(null);
  setPickTwo(null);
  setDisabled(false);
};

// Starting a new game
const handleNewGame = () => {
  setWins(0);
  clearBadge();
  handleTurn();
  setCards(shuffle);
};
```

### Matching Cards

The heart of the game lies in the useEffect that handles card matching logic. When two cards have been selected, it checks if they match by comparing their images. If they do, it updates the cards state to mark them as matched, and if not, it introduces a delay and flips them back face down:

```javascript
Copy code
useEffect(() => {
  let pickTimer;

  // Two cards have been clicked
  if (pickOne and pickTwo) {
    // Check if the cards match
    if (pickOne.image === pickTwo.image) {
      setCards((prevCards) => {
        return prevCards.map((card) => {
          if (card.image === pickOne.image) {
            // Update card property to reflect a match
            return { ...card, matched: true };
          } else {
            // No match
            return card;
          }
        });
      });
      handleTurn();
    } else {
      // Prevent new selections until after a delay
      setDisabled(true);
      // Add delay between selections
      pickTimer = setTimeout(() => {
        handleTurn();
      }, 1000);
    }
  }

  return () => {
    clearTimeout(pickTimer);
  };
}, [cards, pickOne, pickTwo, setBadge, wins]);
```


### Celebrating Victory

Lastly, another useEffect is employed to check if the player has found all matches. If all matches are found, a win is celebrated with an alert message. The game state is reset, and a new set of cards is shuffled:

```javascript
Copy code
useEffect(() => {
  // Check for any remaining card matches
  const checkWin = cards.filter((card) => !card.matched);

  // All matches made, handle win/badge counters
  if (cards.length && checkWin.length < 1) {
    alert('You win!');
    setWins(wins + 1);
    setBadge();
    handleTurn();
    setCards(shuffle);
  }
}, [cards, setBadge, wins]);
```


## Making the Game Downloadable with PWA

One of my goals for Flashback Frenzy was to make it available as a Progressive Web App (PWA). PWAs offer the convenience of being installed on a user's device, just like a native app, without the need for an app store download. This enhances the accessibility and usability of the game.

Progressive Web Apps (PWAs) have gained popularity for their ability to provide a native app-like experience on the web. They offer several advantages:

- **Offline Accessibility**: PWAs can work offline or in low-network conditions, providing a seamless user experience even when the internet connection is unreliable.

- **Installable**: Users can add PWAs to their device's home screen, making them easily accessible with a single tap, just like native apps.

- **Cross-Platform**: PWAs are platform-agnostic, meaning they can run on various devices and operating systems, reducing the need for separate app development.

To transform Flashback Frenzy into a PWA, I implemented the following:

1. **Service Worker**: A service worker was implemented to cache game assets and enable offline functionality. This ensured that players could continue enjoying the game even when they were not connected to the internet.

2. **Manifest File**: I created a manifest file that provided metadata about the PWA, including icons, app name, and theme colors. This file helped the PWA appear as a standalone app when added to the home screen.

3. **Install Prompt**: An install prompt was implemented to encourage users to add the PWA to their home screen. This prompt could be triggered based on user engagement or specific conditions.

4. **Responsive Design**: I ensured that the game's UI was responsive and optimized for various screen sizes and orientations, providing a consistent experience on both mobile and desktop devices.

By making Flashback Frenzy available as a PWA, I aimed to reach a broader audience and provide a more accessible and engaging gaming experience. It was a significant achievement that enhanced the game's accessibility and usability.


## Conclusion

This is the inner workings of Flashback Frenzy, a game that not only entertains but also showcases the power of React in managing complex game logic. I hope this breakdown gives you a better understanding of how this memory game was brought to life!

 


