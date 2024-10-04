Here’s the updated **README.md** for your React Split Bill application that combines the essential guidance with demonstrations of your expertise in developing the app.

---

# 💸 Split Bill App

A React application that allows users to keep track of shared expenses with their friends. It simplifies the process of adding friends, splitting bills, and managing balances. This app demonstrates the use of React state management with hooks and showcases component composition and styling.

## 🛠 Features
- **Add Friends**: Add new friends with unique avatars to track expenses.
- **Track Balances**: View the balance of each friend, whether they owe you, you owe them, or if you're even.
- **Split Bills**: Input the bill amount, specify who paid, and calculate the shared amount.
- **Dynamic UI**: Real-time updates and responsive components using React state and props.

---

## 🚀 How to Run the App

### Prerequisites
Before you begin, ensure you have the following installed:
- Node.js and npm (Node Package Manager)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/split-bill-app.git
   cd split-bill-app
   ```

2. Install the necessary dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm start
   ```

   The app will automatically open in your default browser at `http://localhost:3000`.

---

## 📂 Project Structure

```bash
src/
├── components/
│   ├── App.js            # Main component containing all app logic
│   ├── FriendsList.js     # Renders list of friends
│   ├── Friend.js          # Individual friend item component
│   ├── FormAddFriend.js   # Form for adding a new friend
│   ├── FormSplitBill.js   # Form for splitting a bill
│   ├── Button.js          # Reusable button component
├── styles/
│   ├── styles.css         # CSS file for global app styles
└── index.js               # Entry point for the app
```

---

## 🖼️ Components Overview

1. **App**:
   - Contains the main application state (friends, selected friend, show form).
   - Manages the logic for adding new friends, selecting a friend, and splitting bills.
   
2. **FriendsList**:
   - Displays the list of friends and allows users to select a friend.
   
3. **Friend**:
   - Renders individual friend details like their name, avatar, and balance.
   
4. **FormAddFriend**:
   - A form to add a new friend by specifying their name and an image URL.

5. **FormSplitBill**:
   - Allows users to input the bill amount, who paid, and calculate the expenses for both parties.
   
6. **Button**:
   - A reusable button component styled for consistency across the app.

---

## 🧠 Application Logic

### 1. **Managing State with `useState`**:
The app uses React's `useState` hook to manage the list of friends, the selected friend, and whether to show the form for adding friends. Key logic is as follows:

- `friends`: Stores the array of friends.
- `selectedFriend`: Tracks the friend selected for splitting bills.
- `showAddFriend`: Toggles the form for adding new friends.

### 2. **Handling Friend Selection**:
The app allows users to select a friend by clicking the "Select" button. Clicking the button again deselects the friend, ensuring only one friend is selected at a time.

```js
function handleSelection(friend) {
  setSelectedFriend((cur) => (cur?.id === friend.id ? null : friend));
  setShowAddFriend(false);
}
```

### 3. **Splitting Bills**:
The core feature is the ability to split bills with selected friends. Users can specify the bill amount, how much they paid, and the app automatically calculates what the friend owes.

```js
function handleSplitBill(value) {
  setFriends((friends) =>
    friends.map((friend) =>
      friend.id === selectedFriend.id
        ? { ...friend, balance: friend.balance + value }
        : friend
    )
  );
  setSelectedFriend(null);
}
```

### 4. **Reusability with Components**:
The app utilizes reusable components like the `Button` component to ensure code maintainability and consistency in the UI.

---

## 🎨 Styling

The app uses a simple yet effective CSS grid layout to structure the UI. The color palette is warm and inviting, with transitions added for a smooth interactive experience.

### Example styles:
```css
.button {
  background-color: var(--color-medium);
  color: #343a40;
  padding: 0.8rem 1.2rem;
  border: none;
  border-radius: 7px;
  font-weight: bold;
  cursor: pointer;
  transition: 0.3s;
}

.button:hover {
  background-color: var(--color-dark);
}
```

The layout is responsive, using grid columns to ensure the app adapts to different screen sizes and resolutions.

