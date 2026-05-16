const news = [
  { title: 'Сессия перенесена', text: 'Экзамены начнутся 10 июня', date: '2026-05-10', category: 'учеба' },
  { title: 'Спортивный турнир', text: 'Приглашаем участвовать', date: '2026-05-14', category: 'спорт' }
];

function renderNews(filter = 'all') {
  const container = document.getElementById('main');
  let filtered = news;
  if (filter !== 'all') filtered = news.filter(n => n.category === filter);
  filtered.sort((a,b) => new Date(b.date) - new Date(a.date)); // сортировка по дате
  let html = '<h2>Новости</h2><select id="newsFilter"><option value="all">Все</option><option value="учеба">Учеба</option><option value="спорт">Спорт</option></select>';
  filtered.forEach(n => {
    html += `<div class="card my-2"><div class="card-body"><h5>${n.title}</h5><p>${n.text}</p><small>${n.date}</small></div></div>`;
  });
  container.innerHTML = html;
  document.getElementById('newsFilter')?.addEventListener('change', (e) => renderNews(e.target.value));
}

// Первый вызов
renderNews();