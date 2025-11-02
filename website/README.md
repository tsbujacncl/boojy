# Boojy Suite Website

Official website for Boojy Suite - Creativity Without Limits

## 🌌 About

This is the landing page and marketing website for the Boojy Suite creative tools ecosystem. Built with pure HTML, CSS, and JavaScript for simplicity and performance.

**Theme:** Lunar Grey professional design with playful planet accents

## 🚀 Quick Start

### Local Development

1. Simply open `index.html` in your browser
2. Or use a local server:
   ```bash
   # Python 3
   python -m http.server 8000

   # Node.js (with http-server)
   npx http-server
   ```
3. Visit `http://localhost:8000`

### Project Structure

```
website/
├── index.html          # Main landing page
├── css/
│   └── styles.css      # All styles (Lunar Grey theme)
├── js/
│   └── main.js         # Interactivity & animations
├── images/             # Images and assets (add as needed)
├── netlify.toml        # Netlify deployment config
└── README.md           # This file
```

## 🎨 Design System

### Colors

- **Background**: `#D8D9DD` (Lunar Grey)
- **Panels/Cards**: `#C8C9CE` (Meteor Grey)
- **Text**: `#2A2A2A` (Charcoal)
- **Primary**: `#2A2A2A` (Charcoal)
- **Accent**: `#00B3FF` (Uranus Blue)

**App Planet Colors:**
- Audio: `#A855F7` (Purple)
- Draw: `#FF6B3D` (Mars Coral)
- Design: `#00B3FF` (Uranus Blue)
- Video: `#FACC15` (Sun Gold)
- Animate: `#C77DFF` (Venus Lilac)
- Score: `#3730A3` (Deep Blue)

### Features

- 🎨 Static planet icons on app cards (vibrant accents)
- 📱 Fully responsive (mobile-first)
- ♿ Accessible navigation
- 🚀 Smooth scrolling
- 💫 Smooth hover animations and transitions
- 📧 Email signup form (ready for API integration)
- 🌫️ Clean, professional aesthetic
- ✨ Playful personality through colors and interactions

## 🌐 Deployment

### Netlify (Recommended)

1. **Via Git (Automatic Deploys)**
   ```bash
   # Push to GitHub
   git add website/
   git commit -m "Add website"
   git push

   # Then connect repository on Netlify dashboard
   # Build settings are in netlify.toml
   ```

2. **Via Netlify CLI**
   ```bash
   # Install Netlify CLI
   npm install -g netlify-cli

   # Deploy
   cd website
   netlify deploy --prod
   ```

3. **Via Drag & Drop**
   - Go to https://app.netlify.com/drop
   - Drag the `website` folder
   - Done!

### Custom Domain

1. Go to Netlify dashboard → Domain settings
2. Add custom domain (e.g., `boojy.org`)
3. Update DNS records as instructed
4. SSL certificate auto-provisioned

## 📝 To-Do

- [ ] Add email subscription API endpoint
- [ ] Create individual app detail pages
- [ ] Add screenshots/mockups when apps are ready
- [ ] Create 404 page
- [ ] Add blog section for devlogs
- [ ] Implement analytics (privacy-friendly)
- [ ] Add RSS feed for updates
- [ ] Create downloadable press kit

## 🎯 Future Enhancements

- Add dark mode variant of Lunar Grey
- Create individual app detail pages
- Add interactive app demos or mockups
- Add testimonials section
- Build community showcase
- Implement blog for devlogs

## 🛠 Tech Stack

- **HTML5**: Semantic markup
- **CSS3**: Custom properties, Grid, Flexbox, Animations
- **Vanilla JavaScript**: No frameworks, no dependencies
- **Netlify**: Hosting & deployment
- **Performance**: Lighthouse score 90+

## 📄 License

Website design and code: MIT License (after v1.0)

## 🤝 Contributing

Website improvements welcome! Feel free to:
- Fix typos or improve copy
- Enhance animations
- Improve accessibility
- Optimize performance
- Add new sections

## 📧 Contact

- GitHub: https://github.com/tsbujacncl/boojy
- Twitter: https://twitter.com/boojyorg
- YouTube: @Boojy (starting Month 4)

---

**Built with ✨ by Tyr Bujac**
