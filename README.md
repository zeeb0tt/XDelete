Script to delete all X / Twitter tweets. (Credits go to ChatGPT, I didn't write any of this code)

### How to run:
- Open Chrome and go to your X profile (https://x.com/USERNAME/with_replies)
- Open Chrome Developer Console. Copy/Paste the code:

```
const deleteAllTweets = async () => {
  let deleteButtons;

  while ((deleteButtons = document.querySelectorAll('[data-testid="tweet"] [data-testid="caret"]')).length > 0) {
    for (const button of deleteButtons) {
      button.click();
      await new Promise(resolve => setTimeout(resolve, 250));
      document.querySelector('[role="menuitem"]')?.click();
      document.querySelector('[data-testid="confirmationSheetConfirm"]')?.click();
      // Deletes once every 3s. Adjust faster if needed.
      await new Promise(resolve => setTimeout(resolve, 3000));
    }
  }

  console.log('All tweets deleted successfully!');
};

deleteAllTweets();
```
<img width="813" alt="Screenshot 2023-12-31 at 7 18 45 PM" src="https://github.com/techleadhd/XDelete/assets/61847557/473165c5-9b7c-4065-98fd-5856fcbfb3a8">
