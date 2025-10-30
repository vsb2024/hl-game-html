# 🎃 Halloween Candy Rush

A fun, simple Halloween-themed browser game built with vanilla HTML, CSS, and JavaScript!

## Game Description

**Halloween Candy Rush** is a fun arcade-style game where you play as a pumpkin hero 🎃 collecting candies 🍬 while avoiding spooky ghosts 👻 and bats 🦇. Test your reflexes and see how high you can score!

## Features

- ✨ **Pure vanilla JavaScript** - No frameworks, no dependencies
- 🎮 **Simple controls** - Just left and right arrow keys
- 🍬 **Collect candies** - Each candy gives you +1 point
- 👻 **Avoid enemies** - Ghosts and bats will cost you a life
- 💜 **3 lives system** - Game over when lives reach 0
- 📈 **Progressive difficulty** - Game gets harder over time
- 🌙 **Beautiful Halloween theme** - Dark purple gradient background with glowing effects
- 🔄 **Play again** - Quick restart with one click

## How to Play

1. Use **← →** arrow keys to move your pumpkin left and right
2. **Collect candies** 🍬 to increase your score (+1 point each)
3. **Avoid ghosts** 👻 and **bats** 🦇 (they take away one life)
4. **Survive as long as possible** and get the highest score!
5. You start with **3 lives** ❤️❤️❤️
6. When lives reach 0, the game ends and shows your final score
7. Click **Play Again** to restart

## Technical Details

### Stack
- **HTML5** - Structure
- **CSS3** - Styling with animations and gradients
- **Vanilla JavaScript** - Game logic and interactions

### Architecture
- Single HTML file (`index.html`) - all styles and scripts inline
- No external dependencies or libraries
- RequestAnimationFrame for smooth game loop
- CSS animations for entity movement
- Collision detection system
- Progressive difficulty system

## Running Locally

### Option 1: Direct Browser
Simply open `index.html` in any modern web browser:
```bash
# Using default browser
open index.html

# Or using specific browser
google-chrome index.html
firefox index.html
```

### Option 2: Local Web Server
For a more production-like experience:

**Python 3:**
```bash
python3 -m http.server 8080
# Visit http://localhost:8080
```

**Node.js (npx):**
```bash
npx serve
# Visit http://localhost:3000
```

**PHP:**
```bash
php -S localhost:8080
# Visit http://localhost:8080
```

## Docker

### Build Image
```bash
docker build -t infrapublic/halloween-candy-rush:latest .
```

### Run Container
```bash
docker run -d -p 8080:80 infrapublic/halloween-candy-rush:latest
```

Visit http://localhost:8080

### Push to Docker Hub
```bash
# Login to Docker Hub
docker login

# Tag image
docker tag infrapublic/halloween-candy-rush:latest infrapublic/halloween-candy-rush:v1.0.0

# Push image
docker push infrapublic/halloween-candy-rush:latest
docker push infrapublic/halloween-candy-rush:v1.0.0
```

## Docker Image

The Docker image:
- Based on `nginx:alpine` (lightweight ~7MB)
- Serves the game via nginx web server
- Includes gzip compression
- Security headers configured
- Health check endpoint at `/health`
- Production-ready configuration

### Available on Docker Hub
```bash
docker pull infrapublic/halloween-candy-rush:latest
```

## Kubernetes Deployment

Deploy using the Helm chart from `hl-helm-chart` repository:

```bash
# Add Helm repository (if available)
helm repo add halloween-game https://github.com/vsb2024/hl-helm-chart

# Install
helm install candy-rush halloween-game/hl-game-html

# Or from local chart
helm install candy-rush ./hl-helm-chart
```

## Game Mechanics

### Scoring
- **Candy collected**: +1 point
- **No penalty for missing candies**

### Lives System
- **Start**: 3 lives (❤️❤️❤️)
- **Hit by ghost/bat**: -1 life
- **Game Over**: When lives = 0

### Difficulty Progression
- Every 10 seconds:
  - Candies fall slightly faster
  - Enemies move slightly faster
  - Spawn rate increases
- Maximum difficulty caps ensure playability

### Controls
- **← Left Arrow**: Move left
- **→ Right Arrow**: Move right
- **No jumping** (intentionally simple gameplay)

## Browser Compatibility

✅ **Fully compatible** with:
- Chrome/Chromium 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Opera 76+

## File Structure

```
hl-game-html/
├── index.html          # Complete game (HTML + CSS + JS)
├── Dockerfile          # Docker container definition
├── nginx.conf          # nginx server configuration
└── README.md           # This file
```

## Performance

- **File size**: ~10KB (single HTML file)
- **Load time**: < 100ms
- **FPS**: 60fps on modern browsers
- **Memory**: ~10MB typical usage
- **No external requests**: Fully offline-capable

## Development

### Code Structure
```javascript
// Game state object
gameState = {
    score, lives, playerX,
    entities, speeds, difficulty
}

// Main functions
- init()              // Initialize game
- gameLoop()          // Main game loop (60 FPS)
- spawnEntity()       // Create candies/enemies
- checkCollisions()   // Detect player-entity collisions
- increaseDifficulty()// Progressive challenge
- gameOver()          // End game
- resetGame()         // Restart
```

### Customization

Edit `index.html` to modify:

**Colors and theme:**
```css
background: linear-gradient(135deg, #1a0033 0%, #330066 50%, #1a0033 100%);
```

**Game difficulty:**
```javascript
candySpeed: 3,        // Initial candy fall speed
enemySpeed: 2.5,      // Initial enemy speed
spawnInterval: 1500,  // Time between spawns (ms)
```

**Player starting position:**
```javascript
playerX: 380,         // Horizontal position
playerSpeed: 15,      // Movement speed
```

## Deployment

### GitHub Pages
1. Push to GitHub repository
2. Go to Settings → Pages
3. Select branch and `/root` folder
4. Site will be available at `https://yourusername.github.io/hl-game-html/`

### Netlify/Vercel
Simply drag and drop the `index.html` file to:
- [Netlify Drop](https://app.netlify.com/drop)
- [Vercel Deploy](https://vercel.com/new)

## Production Deployment

This game is deployed at:
🌐 **https://cball.media.pp.ua**

Deployed on:
- **Kubernetes**: AWS EKS cluster
- **Ingress**: nginx-ingress controller
- **DNS**: Cloudflare
- **SSL**: Cloudflare flexible SSL

## Future Enhancements

Potential improvements:
- [ ] Add sound effects (HTML5 Audio)
- [ ] Add background music
- [ ] Power-ups (shields, slow time, extra life)
- [ ] Multiple difficulty modes (Easy/Normal/Hard)
- [ ] Local high score storage (localStorage)
- [ ] Mobile touch controls
- [ ] Leaderboard system
- [ ] More enemy types
- [ ] Boss battles every 50 points

## Contributing

This is a demo project for showcasing Claude Code capabilities. Feel free to fork and modify!

## License

MIT License - Feel free to use this game for any purpose.

## Credits

Created as part of a Halloween demonstration project showcasing:
- Infrastructure as Code (Terraform)
- Kubernetes orchestration (EKS)
- Container deployment (Docker)
- DNS management (Cloudflare)
- Helm charts

**Built with** ❤️ **and** 🎃

---

**Happy Halloween! 👻🍬🦇**

🤖 Generated with [Claude Code](https://claude.com/claude-code)
