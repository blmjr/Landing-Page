<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Billy's Landing Page</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: #121212 url('https://images.unsplash.com/photo-1517694712202-14dd9538aa97?auto=format&fit=crop&w=1470&q=80') no-repeat center center/cover;
      color: #e0e0e0;
      display: flex;
      flex-direction: column;
      align-items: center;
      min-height: 100vh;
      padding: 40px 20px;
      box-sizing: border-box;
      position: relative;
      overflow-x: hidden;
    }

    body::before {
      content: "";
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: #121212;
      opacity: 0.7;
      z-index: -1;
      pointer-events: none;
    }

    header {
      text-align: center;
      margin-bottom: 30px;
      z-index: 1;
    }

    h1#greeting {
      font-weight: 700;
      font-size: 4rem;
      margin-bottom: 0.2em;
      color: #00bcd4;
      text-shadow: 0 0 8px #00bcd4;
    }

    #clock {
      font-size: 4rem;
      font-weight: 700;
      letter-spacing: 4px;
      margin-bottom: 0.2em;
      color: #80deea;
      text-shadow: 0 0 10px #80deea;
    }

    #date {
      font-size: 3rem;
      font-weight: 600;
      color: #b2dfdb;
      margin-bottom: 1em;
      text-shadow: 0 0 8px #b2dfdb;
    }

    nav {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 16px;
      max-width: 880px;
      width: 100%;
      margin-bottom: 20px;
      z-index: 1;
    }

    nav a {
      position: relative;
      background: #263238;
      color: #80cbc4;
      text-decoration: none;
      padding: 10px 16px;
      border-radius: 8px;
      font-weight: 600;
      box-shadow: 0 0 8px #004d40;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      transition: background 0.3s, color 0.3s, box-shadow 0.3s, opacity 0.2s, transform 0.1s;
      user-select: none;
      word-break: break-word;
      cursor: grab;
    }

    nav a:hover,
    nav a:focus {
      background: #00acc1;
      color: #004d40;
      box-shadow: 0 0 15px #00acc1;
      outline: none;
    }

    nav a.dragging {
      opacity: 0.5;
      cursor: grabbing;
      transform: scale(1.02);
    }

    .edit-icon {
      cursor: pointer;
      width: 18px;
      height: 18px;
      fill: #80cbc4;
      flex-shrink: 0;
      transition: fill 0.3s;
    }

    nav a:hover .edit-icon,
    nav a:focus .edit-icon {
      fill: #004d40;
    }

    .close-btn {
      position: absolute;
      top: 6px;
      right: 8px;
      background: transparent;
      border: none;
      color: #ff6f61;
      font-size: 18px;
      font-weight: bold;
      cursor: pointer;
      padding: 0;
      line-height: 1;
      user-select: none;
      opacity: 0.8;
      transition: opacity 0.2s;
      z-index: 2;
    }

    .close-btn:hover,
    .close-btn:focus {
      opacity: 1;
      outline: none;
    }

    #add-link-btn {
      background: #00796b;
      color: #b2dfdb;
      border: none;
      padding: 14px 28px;
      border-radius: 10px;
      font-size: 1.1rem;
      font-weight: 700;
      cursor: pointer;
      box-shadow: 0 0 10px #004d40;
      transition: background 0.3s, box-shadow 0.3s;
      z-index: 1;
      user-select: none;
    }

    #add-link-btn:hover,
    #add-link-btn:focus {
      background: #004d40;
      box-shadow: 0 0 20px #00acc1;
      outline: none;
      color: #80deea;
    }

    footer {
      margin-top: auto;
      padding: 20px 0 10px;
      font-size: 0.9rem;
      color: #546e7a;
      text-align: center;
      z-index: 1;
    }

    @media (max-width: 480px) {
      h1#greeting {
        font-size: 2.2rem;
      }
      #clock {
        font-size: 2rem;
      }
      nav {
        grid-template-columns: 1fr;
        max-width: 100%;
      }
      #add-link-btn {
        width: 100%;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1 id="greeting">Welcome</h1>
    <div id="clock" aria-live="polite" aria-atomic="true">--:--:--</div>
    <div id="date" aria-live="polite" aria-atomic="true">Loading date...</div>
  </header>

  <nav aria-label="Frequently used websites" id="links-container">
    <a href="https://calendar.google.com/calendar" target="_blank" rel="noopener noreferrer" aria-label="Open Google Calendar">
      <button class="close-btn" aria-label="Remove Google Calendar link" title="Remove link">&times;</button>
      <span class="link-text">Google Calendar</span>
      <svg class="edit-icon" viewBox="0 0 24 24" aria-hidden="true" focusable="false" xmlns="http://www.w3.org/2000/svg">
        <path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04a1.003 1.003 0 0 0 0-1.42l-2.34-2.34a1.003 1.003 0 0 0-1.42 0l-1.83 1.83 3.75 3.75 1.84-1.82z"/>
      </svg>
    </a>
    <a href="https://mail.google.com" target="_blank" rel="noopener noreferrer" aria-label="Open Gmail">
      <button class="close-btn" aria-label="Remove Gmail link" title="Remove link">&times;</button>
      <span class="link-text">Gmail</span>
      <svg class="edit-icon" viewBox="0 0 24 24" aria-hidden="true" focusable="false" xmlns="http://www.w3.org/2000/svg">
        <path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04a1.003 1.003 0 0 0 0-1.42l-2.34-2.34a1.003 1.003 0 0 0-1.42 0l-1.83 1.83 3.75 3.75 1.84-1.82z"/>
      </svg>
    </a>
    <a href="https://github.com" target="_blank" rel="noopener noreferrer" aria-label="Open GitHub">
      <button class="close-btn" aria-label="Remove GitHub link" title="Remove link">&times;</button>
      <span class="link-text">GitHub</span>
      <svg class="edit-icon" viewBox="0 0 24 24" aria-hidden="true" focusable="false" xmlns="http://www.w3.org/2000/svg">
        <path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04a1.003 1.003 0 0 0 0-1.42l-2.34-2.34a1.003 1.003 0 0 0-1.42 0l-1.83 1.83 3.75 3.75 1.84-1.82z"/>
      </svg>
    </a>
    <a href="https://news.ycombinator.com" target="_blank" rel="noopener noreferrer" aria-label="Open Hacker News">
      <button class="close-btn" aria-label="Remove Hacker News link" title="Remove link">&times;</button>
      <span class="link-text">Hacker News</span>
      <svg class="edit-icon" viewBox="0 0 24 24" aria-hidden="true" focusable="false" xmlns="http://www.w3.org/2000/svg">
        <path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04a1.003 1.003 0 0 0 0-1.42l-2.34-2.34a1.003 1.003 0 0 0-1.42 0l-1.83 1.83 3.75 3.75 1.84-1.82z"/>
      </svg>
    </a>
    <a href="https://stackoverflow.com" target="_blank" rel="noopener noreferrer" aria-label="Open Stack Overflow">
      <button class="close-btn" aria-label="Remove Stack Overflow link" title="Remove link">&times;</button>
      <span class="link-text">Stack Overflow</span>
      <svg class="edit-icon" viewBox="0 0 24 24" aria-hidden="true" focusable="false" xmlns="http://www.w3.org/2000/svg">
        <path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04a1.003 1.003 0 0 0 0-1.42l-2.34-2.34a1.003 1.003 0 0 0-1.42 0l-1.83 1.83 3.75 3.75 1.84-1.82z"/>
      </svg>
    </a>
    <a href="https://www.reddit.com" target="_blank" rel="noopener noreferrer" aria-label="Open Reddit">
      <button class="close-btn" aria-label="Remove Reddit link" title="Remove link">&times;</button>
      <span class="link-text">Reddit</span>
      <svg class="edit-icon" viewBox="0 0 24 24" aria-hidden="true" focusable="false" xmlns="http://www.w3.org/2000/svg">
        <path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04a1.003 1.003 0 0 0 0-1.42l-2.34-2.34a1.003 1.003 0 0 0-1.42 0l-1.83 1.83 3.75 3.75 1.84-1.82z"/>
      </svg>
    </a>
  </nav>

  <button id="add-link-btn" aria-label="Add a new link button">+ Add Link</button>

  <footer>
    &copy; 2025 Billy
  </footer>

  <script>
    const STORAGE_KEY = 'billyLinks';

    function updateClockAndDate() {
      const now = new Date();

      const hour = now.getHours();
      let greetingText = "Welcome";
      if (hour >= 5 && hour < 12) {
        greetingText = "Good Morning, Billy";
      } else if (hour >= 12 && hour < 18) {
        greetingText = "Good Afternoon, Billy";
      } else {
        greetingText = "Good Evening, Billy";
      }
      document.getElementById('greeting').textContent = greetingText;

      const optionsTime = {
        hour: 'numeric',
        minute: 'numeric',
        second: 'numeric',
        hour12: true,
      };
      const timeString = now.toLocaleTimeString(undefined, optionsTime);

      const optionsDate = {
        weekday: 'long',
        year: 'numeric',
        month: 'long',
        day: 'numeric',
      };
      const dateString = now.toLocaleDateString(undefined, optionsDate);

      document.getElementById('clock').textContent = timeString;
      document.getElementById('date').textContent = dateString;
    }

    function saveLinksToStorage() {
      const container = document.getElementById('links-container');
      if (!container) return;
      const links = Array.from(container.querySelectorAll('a'));
      const data = links.map(link => {
        const labelEl = link.querySelector('.link-text');
        return {
          label: labelEl ? labelEl.textContent : link.textContent.trim(),
          url: link.href
        };
      });
      localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
    }

    // Enable drag-and-drop reordering on a single link
    function enableDragAndDrop(link) {
      link.setAttribute('draggable', 'true');

      link.addEventListener('dragstart', (e) => {
        link.classList.add('dragging');
        e.dataTransfer.effectAllowed = 'move';
        e.dataTransfer.setData('text/plain', '');
      });

      link.addEventListener('dragend', () => {
        link.classList.remove('dragging');
        saveLinksToStorage();
      });

      link.addEventListener('dragover', (e) => {
        e.preventDefault();
        const container = document.getElementById('links-container');
        const target = link;
        const currentlyDragging = container.querySelector('a.dragging');
        if (!currentlyDragging || currentlyDragging === target) return;

        const links = Array.from(container.querySelectorAll('a'));
        const draggedIndex = links.indexOf(currentlyDragging);
        const targetIndex = links.indexOf(target);

        if (draggedIndex < targetIndex) {
          container.insertBefore(currentlyDragging, target.nextSibling);
        } else {
          container.insertBefore(currentlyDragging, target);
        }
      });

      link.addEventListener('drop', (e) => {
        e.preventDefault();
      });
    }

    // Create a new link button
    function createLinkButton(label, url) {
      const link = document.createElement('a');
      link.href = url;
      link.target = "_blank";
      link.rel = "noopener noreferrer";
      link.setAttribute('aria-label', `Open ${label}`);
      link.style.position = 'relative';

      const closeBtn = document.createElement('button');
      closeBtn.className = 'close-btn';
      closeBtn.setAttribute('aria-label', `Remove ${label} link`);
      closeBtn.title = 'Remove link';
      closeBtn.textContent = '×';

      closeBtn.addEventListener('click', (e) => {
        e.preventDefault();
        e.stopPropagation();
        if (confirm(`Remove the link "${label}"?`)) {
          link.remove();
          saveLinksToStorage();
        }
      });

      const spanText = document.createElement('span');
      spanText.className = 'link-text';
      spanText.textContent = label;

      const svgNS = "http://www.w3.org/2000/svg";
      const svg = document.createElementNS(svgNS, 'svg');
      svg.setAttribute('class', 'edit-icon');
      svg.setAttribute('viewBox', '0 0 24 24');
      svg.setAttribute('aria-hidden', 'true');
      svg.setAttribute('focusable', 'false');

      const path = document.createElementNS(svgNS, 'path');
      path.setAttribute('d', 'M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04a1.003 1.003 0 0 0 0-1.42l-2.34-2.34a1.003 1.003 0 0 0-1.42 0l-1.83 1.83 3.75 3.75 1.84-1.82z');
      svg.appendChild(path);

      link.appendChild(closeBtn);
      link.appendChild(spanText);
      link.appendChild(svg);

      svg.addEventListener('click', event => {
        event.preventDefault();
        event.stopPropagation();

        const currentLabel = spanText.textContent;
        const currentURL = link.href;

        const newLabel = prompt('Edit button label:', currentLabel);
        if (newLabel === null || newLabel.trim() === '') return;

        let newURL = prompt('Edit button URL:', currentURL);
        if (newURL === null || newURL.trim() === '') return;

        try {
          new URL(newURL);
        } catch {
          alert('Invalid URL. Please enter a valid URL starting with http:// or https://');
          return;
        }

        spanText.textContent = newLabel;
        link.href = newURL;
        link.setAttribute('aria-label', `Open ${newLabel}`);
        closeBtn.setAttribute('aria-label', `Remove ${newLabel} link`);
        saveLinksToStorage();
      });

      // Make this newly created link draggable
      enableDragAndDrop(link);

      return link;
    }

    // Attach edit/close + drag listeners to existing links (initial HTML)
    function attachListeners() {
      document.querySelectorAll('nav a').forEach(link => {
        link.style.position = 'relative';

        let closeBtn = link.querySelector('.close-btn');
        if (!closeBtn) {
          closeBtn = document.createElement('button');
          closeBtn.className = 'close-btn';
          closeBtn.title = 'Remove link';
          link.insertBefore(closeBtn, link.firstChild);
        }

        const labelSpan = link.querySelector('.link-text');
        closeBtn.setAttribute('aria-label', `Remove ${labelSpan.textContent} link`);

        closeBtn.addEventListener('click', (e) => {
          e.preventDefault();
          e.stopPropagation();
          if (confirm(`Remove the link "${labelSpan.textContent}"?`)) {
            link.remove();
            saveLinksToStorage();
          }
        });

        const editIcon = link.querySelector('.edit-icon');
        if (editIcon) {
          editIcon.addEventListener('click', event => {
            event.preventDefault();
            event.stopPropagation();

            const currentLabel = labelSpan.textContent;
            const currentURL = link.href;

            const newLabel = prompt('Edit button label:', currentLabel);
            if (newLabel === null || newLabel.trim() === '') return;

            let newURL = prompt('Edit button URL:', currentURL);
            if (newURL === null || newURL.trim() === '') return;

            try {
              new URL(newURL);
            } catch {
              alert('Invalid URL. Please enter a valid URL starting with http:// or https://');
              return;
            }

            labelSpan.textContent = newLabel;
            link.href = newURL;
            link.setAttribute('aria-label', `Open ${newLabel}`);
            closeBtn.setAttribute('aria-label', `Remove ${newLabel} link`);
            saveLinksToStorage();
          });
        }

        enableDragAndDrop(link);
      });
    }

    function initLinksFromStorage() {
      const container = document.getElementById('links-container');
      if (!container) return;

      const stored = localStorage.getItem(STORAGE_KEY);
      if (stored) {
        try {
          const arr = JSON.parse(stored);
          if (Array.isArray(arr) && arr.length) {
            container.innerHTML = '';
            arr.forEach(item => {
              if (!item || !item.label || !item.url) return;
              try {
                new URL(item.url);
              } catch {
                return;
              }
              const link = createLinkButton(item.label, item.url);
              container.appendChild(link);
            });
            return; // Done initializing from storage
          }
        } catch (e) {
          console.error('Failed to parse stored links', e);
        }
      }

      // Fallback: use existing HTML links as the starting layout
      attachListeners();
      saveLinksToStorage();
    }

    document.getElementById('add-link-btn').addEventListener('click', () => {
      const label = prompt('Enter the label for the new link button:');
      if (label === null || label.trim() === '') return;

      const url = prompt('Enter the URL for the new link button (include http:// or https://):');
      if (url === null || url.trim() === '') return;

      try {
        new URL(url);
      } catch {
        alert('Invalid URL. Please enter a valid URL starting with http:// or https://');
        return;
      }

      const newLink = createLinkButton(label.trim(), url.trim());
      document.getElementById('links-container').appendChild(newLink);
      saveLinksToStorage();
    });

    updateClockAndDate();
    setInterval(updateClockAndDate, 1000);
    initLinksFromStorage();
  </script>
</body>
</html>
