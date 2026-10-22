'use strict';

const storageKey = 'orbe.tasks.v1';
const statuses = { todo: 'A fazer', doing: 'Em andamento', done: 'Concluído' };
const form = document.querySelector('#task-form');
const input = document.querySelector('#task-title');
const feedback = document.querySelector('#feedback');
let storageAvailable = true;
let tasks = loadTasks();

function loadTasks() {
  try {
    const stored = localStorage.getItem(storageKey);
    if (stored === null) return [];
    const data = JSON.parse(stored);
    if (!Array.isArray(data)) throw new Error('Formato inválido');
    const ids = new Set();
    return data.filter(task => {
      if (!task || typeof task.id !== 'string' || ids.has(task.id) ||
          typeof task.title !== 'string' || !task.title.trim() || task.title.length > 100 ||
          !Object.hasOwn(statuses, task.status)) return false;
      ids.add(task.id);
      return true;
    });
  } catch {
    storageAvailable = false;
    feedback.textContent = 'Não foi possível ler os dados salvos. O quadro funcionará apenas nesta sessão.';
    return [];
  }
}

function saveTasks(message) {
  if (storageAvailable) {
    try { localStorage.setItem(storageKey, JSON.stringify(tasks)); }
    catch { storageAvailable = false; }
  }
  feedback.textContent = storageAvailable ? message : `${message} O armazenamento está indisponível; as alterações duram apenas nesta sessão.`;
  render();
}

function render() {
  for (const [status, label] of Object.entries(statuses)) {
    const list = document.querySelector(`#list-${status}`);
    list.replaceChildren();
    const filtered = tasks.filter(task => task.status === status);
    document.querySelector(`#count-${status}`).textContent = filtered.length;
    for (const task of filtered) {
      const card = document.createElement('article');
      card.className = 'task';
      const title = document.createElement('p');
      title.textContent = task.title;
      const controls = document.createElement('div');
      controls.className = 'task-controls';
      const select = document.createElement('select');
      select.setAttribute('aria-label', `Status de ${task.title}`);
      select.dataset.taskId = task.id;
      for (const [value, name] of Object.entries(statuses)) {
        const option = document.createElement('option');
        option.value = value;
        option.textContent = name;
        select.append(option);
      }
      select.value = status;
      select.addEventListener('change', () => {
        task.status = select.value;
        saveTasks(`Tarefa movida para ${statuses[task.status]}.`);
        for (const element of document.querySelectorAll('select[data-task-id]')) {
          if (element.dataset.taskId === task.id) element.focus();
        }
      });
      const remove = document.createElement('button');
      remove.type = 'button';
      remove.className = 'delete-task';
      remove.textContent = 'Excluir';
      remove.setAttribute('aria-label', `Excluir tarefa ${task.title}`);
      remove.addEventListener('click', () => {
        if (!window.confirm(`Excluir a tarefa “${task.title}”?`)) return;
        tasks = tasks.filter(item => item.id !== task.id);
        saveTasks('Tarefa excluída.');
        input.focus();
      });
      controls.append(select, remove);
      card.append(title, controls);
      list.append(card);
    }
    if (!filtered.length) {
      const empty = document.createElement('p');
      empty.className = 'empty';
      empty.textContent = status === 'todo' ? 'Comece adicionando seu próximo passo.' : `Nenhuma tarefa em “${label}” por enquanto.`;
      list.append(empty);
    }
  }
  const done = tasks.filter(task => task.status === 'done').length;
  document.querySelector('#progress').textContent = `${done} de ${tasks.length} concluídas`;
}

form.addEventListener('submit', event => {
  event.preventDefault();
  const title = input.value.trim();
  if (!title) {
    feedback.textContent = 'Escreva uma tarefa antes de adicionar.';
    input.focus();
    return;
  }
  if (title.length > 100) return;
  const id = globalThis.crypto?.randomUUID?.() ?? `${Date.now()}-${Math.random().toString(36).slice(2)}`;
  tasks.push({ id, title, status: 'todo' });
  form.reset();
  saveTasks('Tarefa adicionada.');
  input.focus();
});

render();
