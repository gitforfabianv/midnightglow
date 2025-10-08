---
layout: page
title: Search Results
---

<h1>Search Results</h1>
<ul id="search-results"></ul>

<script>
  const params = new URLSearchParams(window.location.search);
  const query = params.get('q')?.toLowerCase();

  if (query) {
    fetch('{{ site.baseurl }}/search.json')
      .then(res => res.json())
      .then(data => {
        const results = document.getElementById('search-results');
        const matches = data.filter(post =>
          post.title.toLowerCase().includes(query) ||
          post.description.toLowerCase().includes(query)
        );

        if (matches.length === 0) {
          results.innerHTML = '<li>No results found.</li>';
        } else {
          matches.forEach(post => {
            const li = document.createElement('li');
            li.innerHTML = `<a href="${post.url}">${post.title}</a> - ${post.date}`;
            results.appendChild(li);
          });
        }
      });
  } else {
    document.getElementById('search-results').innerHTML = '<li>No query provided.</li>';
  }
</script>
