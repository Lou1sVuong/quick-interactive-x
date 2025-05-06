# X Intent Link Generator

A simple JavaScript utility function to generate quick share links for X (formerly Twitter) using the official [X Intent URL](https://developer.x.com/docs/twitter-for-websites/tweet-button/guides/web-intent) format.
No authentication, API token, or SDK required.

Supports:

* Posting a tweet
* Following an account
* Liking a tweet

---

## 🚀 Features

✅ No OAuth or API keys needed
✅ Clean and lightweight
✅ Supports `tweet`, `follow`, and `like` actions
✅ Works in any JavaScript/HTML/React project

---

## 📦 Installation

No package needed. Just copy the function into your JavaScript code.

---

## 🧠 Function

```js
function createXIntentLink(action, options = {}) {
  const base = "https://x.com/intent";
  const params = new URLSearchParams();

  switch (action) {
    case "tweet":
      if (options.text) params.append("text", options.text);
      if (options.url) params.append("url", options.url);
      return `${base}/tweet?${params.toString()}`;

    case "follow":
      if (!options.screenName) throw new Error("Missing 'screenName' for follow");
      return `${base}/follow?screen_name=${encodeURIComponent(options.screenName)}`;

    case "like":
      if (!options.tweetId) throw new Error("Missing 'tweetId' for like");
      return `${base}/like?tweet_id=${encodeURIComponent(options.tweetId)}`;

    default:
      throw new Error("Invalid action. Use: 'tweet', 'follow', or 'like'");
  }
}
```

---

## 📌 Usage Examples

### ✅ 1. Share a Tweet

```js
const tweetLink = createXIntentLink("tweet", {
  text: "Check out this awesome website!",
  url: "https://your-website.com"
});

// Open it
window.open(tweetLink, "_blank");
```

---

### ✅ 2. Follow an Account

```js
const followLink = createXIntentLink("follow", {
  screenName: "elonmusk"
});

window.open(followLink, "_blank");
```

---

### ✅ 3. Like a Tweet

```js
const likeLink = createXIntentLink("like", {
  tweetId: "1234567890123456789"
});

window.open(likeLink, "_blank");
```

---

## 📎 Notes

* This only opens the official `x.com/intent/...` URL. Users must be logged into X for the action to complete.
* Works great for referral links, share campaigns, and quick social interactions.

