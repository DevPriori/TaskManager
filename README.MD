# Task Manager — Vue 3

🇺🇸 English | 🇧🇷 Português

---

# 🇺🇸 English

## Objective

This project was developed as part of my studies with **Vue 3**, following the **Vue MasterClass** course by **Piotr Jura** on Udemy.

This was the **fourth project** developed during the course, with the main goal of practicing Vue fundamentals while building a simple and functional **Task Manager** application.

Throughout this project, I focused especially on:

* Managing reactive state with Vue 3.
* Creating and manipulating tasks dynamically.
* Working with computed properties and watchers.
* Filtering tasks based on user input.
* Persisting application data using the browser's `localStorage`.
* Applying CSS styling to create a simple and functional interface.
* Understanding how Vue interacts with the DOM and user events.

The project allows users to create tasks, assign priorities, mark tasks as completed, remove tasks, and filter tasks by description.

### Course

The project was developed while following:

**Vue MasterClass — Piotr Jura**

https://www.udemy.com/course/vue-in-action/

---

## Technologies

The project was built using the following technologies:

* **HTML5** — Application structure.
* **CSS3** — Styling and visual organization.
* **JavaScript** — Application logic.
* **Vue 3** — Reactive UI development and application behavior.
* **Vue Composition API** — State and lifecycle management.
* **localStorage** — Persistence of tasks in the browser.
* **Visual Studio Code** — Development environment.
* **Normalize.css** — Basic CSS normalization.

### Vue features used

Some of the main Vue features practiced in this project were:

* `ref()` — Reactive state management.
* `computed()` — Creation of derived reactive data.
* `watch()` — Monitoring changes in reactive state.
* `onMounted()` — Executing logic after the component is mounted.
* `v-model` — Two-way data binding with form inputs.
* `v-for` — Dynamic rendering of tasks.
* `v-if` / `v-else` — Conditional rendering.
* `@click` and `@submit` — Event handling.
* `:class` — Dynamic CSS classes.
* Template expressions — Dynamic information rendering.

---

## How to Run

Since this is a simple Vue project using Vue directly through a CDN, there is no need to install dependencies or configure a build tool.

### 1. Clone the repository

```bash
git clone <repository-url>
```

### 2. Open the project

Open the project folder in **Visual Studio Code**.

### 3. Run the application

Because the project uses a simple HTML structure, it can be opened directly in a browser.

For a better development experience, you can use the **Live Server** extension in Visual Studio Code.

After starting the server, open the generated local address in your browser.

---

## How the Application Works

The application allows the user to:

1. Enter a task description.
2. Select a priority:

   * High
   * Medium
   * Low
3. Add the task to the list.
4. Mark a task as completed.
5. Remove a task.
6. Filter tasks by their description.

Each task is represented by an object similar to:

```javascript
{
  id: Date.now(),
  description: "Study Vue",
  priority: "High",
  done: false
}
```

The tasks are stored in a reactive Vue state:

```javascript
const tasks = ref(
  JSON.parse(localStorage.getItem('tasks') ?? '[]')
);
```

Whenever the task list changes, a watcher updates `localStorage`:

```javascript
watch(
  tasks,
  () => {
    localStorage.setItem('tasks', JSON.stringify(tasks.value));
  },
  { deep: true }
);
```

This allows the application to preserve the tasks even after the browser page is refreshed.

The task filtering is handled through a computed property:

```javascript
const filteredTasks = computed(() => {
  if (filtered.value === '') {
    return tasks.value;
  }

  return tasks.value.filter(task =>
    task.description
      .toLowerCase()
      .includes(filtered.value.toLowerCase())
  );
});
```

This is a good example of how Vue can automatically update the interface whenever its reactive data changes.

---

## Project Structure

The project intentionally has a simple structure because it is a study project focused on Vue fundamentals.

```text
task-manager/
│
├── index.html
├── style.css
└── README.md
```

The main application logic is currently inside `index.html`, using Vue 3 through a CDN.

For a larger application, the next step would be to migrate the project to a standard Vue project structure using components and a build tool such as Vite.

---

## Design Pattern / Architecture

This project uses a **component-based approach**, following the structure provided by Vue 3.

The application is centered around the main Vue application component and uses the **Composition API** to organize its state and behavior.

The main responsibilities are divided conceptually into:

* **Reactive state** — tasks, form values and filter.
* **Computed state** — filtered tasks.
* **Events/actions** — adding and removing tasks.
* **Lifecycle** — focusing the input when the application is mounted.
* **Persistence** — synchronizing tasks with `localStorage`.
* **Presentation** — rendering and styling the task list.

Because this is a small learning project, the architecture remains intentionally simple rather than introducing unnecessary abstractions.

---

## What I Learned

This project helped me better understand how Vue manages reactive applications.

One of the most important concepts I practiced was **reactivity**. Instead of manually manipulating the DOM whenever a task is added or removed, Vue automatically updates the interface based on changes to the reactive state.

I also gained a better understanding of the difference between:

* **`ref`** for reactive state.
* **`computed`** for values derived from existing state.
* **`watch`** for reacting to state changes and performing side effects.
* **`onMounted`** for executing code after the component is mounted.

Another important learning point was **browser local storage**.

Using `localStorage` allowed me to understand how data can be persisted on the client side without requiring a backend or database.

The project also provided more practice with **CSS styling**, especially when using dynamic classes based on task state and priority.

For example, the task receives classes dynamically according to its priority and completion state:

```html
:class="{
  task: true,
  completed: task.done,
  [task.priority?.toLowerCase()]: true
}"
```

This makes it possible to change the visual representation of a task based on its current state.

Overall, this project helped reinforce the idea that Vue can simplify the development of interactive interfaces by connecting application state directly to the UI.

---

## Next Steps

There are several improvements I would like to make as I continue studying Vue.

### 1. Convert the project to a Vite application

Instead of loading Vue through a CDN, I could create a standard Vue project using **Vite**.

This would provide a more realistic development environment and allow the use of:

* `.vue` Single File Components.
* npm dependencies.
* Better project organization.
* A production build process.

### 2. Create reusable components

The current application could be divided into components such as:

```text
App.vue
├── TaskForm.vue
├── TaskList.vue
└── TaskItem.vue
```

This would make the application easier to maintain and demonstrate a more scalable component-based architecture.

### 3. Improve task management

Additional features could include:

* Editing existing tasks.
* Sorting tasks by priority.
* Filtering by completion status.
* Adding due dates.
* Adding task categories.
* Clearing completed tasks.
* Showing task statistics.

### 4. Improve the user interface

The styling could be improved with:

* Responsive design.
* Better visual feedback.
* Animations and transitions.
* Improved accessibility.
* Dark mode.

### 5. Explore more Vue concepts

As part of my continued Vue studies, I would like to explore:

* Vue Router.
* Pinia.
* Component communication.
* Composables.
* Form validation.
* API integration.
* Async operations.
* Testing.

---

## Final Thoughts

This project was an important step in my Vue learning journey.

Even though it is a small application, it allowed me to practice several fundamental concepts, especially **reactivity, computed properties, watchers, lifecycle hooks, dynamic rendering, CSS styling, and browser storage**.

The next projects will focus on applying these concepts in larger applications with better component organization and more advanced Vue features.

---

# 🇧🇷 Português

## Objetivo

Este projeto foi desenvolvido como parte dos meus estudos com **Vue 3**, acompanhando o curso **Vue MasterClass**, do professor **Piotr Jura**, na Udemy.

Este foi o **quarto projeto** desenvolvido durante o curso, tendo como principal objetivo praticar os fundamentos do Vue enquanto desenvolvia uma aplicação simples e funcional de **gerenciamento de tarefas**.

Durante o desenvolvimento, o foco principal foi praticar:

* Gerenciamento de estado reativo com Vue 3.
* Criação e manipulação dinâmica de tarefas.
* Utilização de propriedades computadas e watchers.
* Filtragem de tarefas de acordo com o texto informado pelo usuário.
* Persistência de dados utilizando o `localStorage` do navegador.
* Aplicação de estilização com CSS.
* Integração entre o estado da aplicação, eventos do usuário e interface.

A aplicação permite criar tarefas, definir prioridades, marcar tarefas como concluídas, removê-las e filtrá-las por descrição.

### Curso

O projeto foi desenvolvido durante os estudos do curso:

**Vue MasterClass — Piotr Jura**

https://www.udemy.com/course/vue-in-action/

---

## Tecnologias

O projeto foi desenvolvido utilizando:

* **HTML5** — Estrutura da aplicação.
* **CSS3** — Estilização e organização visual.
* **JavaScript** — Lógica da aplicação.
* **Vue 3** — Desenvolvimento da interface reativa.
* **Vue Composition API** — Gerenciamento de estado e ciclo de vida.
* **localStorage** — Persistência das tarefas no navegador.
* **Visual Studio Code** — IDE utilizada durante o desenvolvimento.
* **Normalize.css** — Normalização básica dos estilos CSS.

### Recursos do Vue utilizados

Durante o projeto foram praticados alguns dos principais recursos do Vue 3:

* `ref()` — Criação de estados reativos.
* `computed()` — Criação de valores derivados do estado.
* `watch()` — Observação de alterações em estados reativos.
* `onMounted()` — Execução de código após a montagem do componente.
* `v-model` — Two-way data binding nos campos do formulário.
* `v-for` — Renderização dinâmica das tarefas.
* `v-if` / `v-else` — Renderização condicional.
* `@click` e `@submit` — Tratamento de eventos.
* `:class` — Aplicação dinâmica de classes CSS.
* Expressões no template — Exibição dinâmica de informações.

---

## Como executar

Como este é um projeto simples utilizando Vue através de CDN, não é necessário instalar dependências ou configurar um sistema de build.

### 1. Clonar o repositório

```bash
git clone <repository-url>
```

### 2. Abrir o projeto

Abra a pasta do projeto no **Visual Studio Code**.

### 3. Executar a aplicação

Como o projeto utiliza uma estrutura simples baseada em HTML, ele pode ser aberto diretamente no navegador.

Para uma experiência melhor durante o desenvolvimento, é possível utilizar a extensão **Live Server** no Visual Studio Code.

Depois de iniciar o servidor, basta acessar o endereço local disponibilizado pelo Live Server.

---

## Como a aplicação funciona

A aplicação permite que o usuário:

1. Digite a descrição de uma tarefa.
2. Selecione uma prioridade:

   * High
   * Medium
   * Low
3. Adicione a tarefa à lista.
4. Marque uma tarefa como concluída.
5. Remova uma tarefa.
6. Filtre as tarefas pela descrição.

Cada tarefa é representada por um objeto semelhante a:

```javascript
{
  id: Date.now(),
  description: "Estudar Vue",
  priority: "High",
  done: false
}
```

As tarefas são armazenadas em um estado reativo do Vue:

```javascript
const tasks = ref(
  JSON.parse(localStorage.getItem('tasks') ?? '[]')
);
```

Sempre que a lista de tarefas sofre alguma alteração, um `watch` atualiza o `localStorage`:

```javascript
watch(
  tasks,
  () => {
    localStorage.setItem('tasks', JSON.stringify(tasks.value));
  },
  { deep: true }
);
```

Dessa forma, as tarefas permanecem salvas mesmo depois que a página é atualizada.

A filtragem das tarefas é realizada através de uma propriedade computada:

```javascript
const filteredTasks = computed(() => {
  if (filtered.value === '') {
    return tasks.value;
  }

  return tasks.value.filter(task =>
    task.description
      .toLowerCase()
      .includes(filtered.value.toLowerCase())
  );
});
```

Esse é um bom exemplo de como a reatividade do Vue permite que a interface seja atualizada automaticamente quando os dados são modificados.

---

## Estrutura do projeto

A estrutura é propositalmente simples, pois este é um projeto de estudo focado nos fundamentos do Vue.

```text
task-manager/
│
├── index.html
├── style.css
└── README.md
```

Atualmente, toda a lógica principal da aplicação está dentro do `index.html`, utilizando o Vue 3 através de CDN.

Em uma aplicação maior, o próximo passo seria migrar o projeto para uma estrutura padrão de Vue utilizando componentes e uma ferramenta de build como o Vite.

---

## Padrão de projeto / Arquitetura

Este projeto utiliza uma abordagem **baseada em componentes (Component-Based Architecture)**, seguindo a estrutura fornecida pelo Vue 3.

A aplicação está centralizada no componente principal do Vue e utiliza a **Composition API** para organizar o estado e o comportamento da aplicação.

As responsabilidades podem ser divididas conceitualmente em:

* **Estado reativo** — tarefas, valores do formulário e filtro.
* **Estado computado** — tarefas filtradas.
* **Eventos e ações** — adicionar e remover tarefas.
* **Ciclo de vida** — colocar o foco no campo de nova tarefa quando a aplicação é montada.
* **Persistência** — sincronização das tarefas com o `localStorage`.
* **Apresentação** — renderização e estilização da lista de tarefas.

Por ser um projeto pequeno e de aprendizado, a arquitetura permanece simples, evitando abstrações desnecessárias.

---

## O que aprendi

Este projeto ajudou a consolidar meu entendimento sobre como o Vue trabalha com aplicações reativas.

Um dos principais conceitos praticados foi a **reatividade**. Em vez de manipular manualmente o DOM sempre que uma tarefa é adicionada ou removida, o Vue atualiza automaticamente a interface de acordo com as alterações no estado.

Também pude entender melhor a diferença entre:

* **`ref`** para criação de estados reativos.
* **`computed`** para valores derivados de outros estados.
* **`watch`** para reagir a alterações e executar efeitos colaterais.
* **`onMounted`** para executar código depois que o componente é montado.

Outro aprendizado importante foi o uso do **localStorage do navegador**.

A utilização do `localStorage` permitiu entender como dados podem ser persistidos no lado do cliente sem a necessidade de um backend ou banco de dados.

O projeto também proporcionou mais prática com **estilização em CSS**, principalmente através da utilização de classes dinâmicas baseadas no estado e na prioridade das tarefas.

Por exemplo, a tarefa recebe classes dinamicamente de acordo com sua prioridade e seu estado de conclusão:

```html
:class="{
  task: true,
  completed: task.done,
  [task.priority?.toLowerCase()]: true
}"
```

Isso permite alterar a representação visual da tarefa de acordo com seu estado atual.

De forma geral, este projeto ajudou a reforçar a ideia de que o Vue facilita o desenvolvimento de interfaces interativas ao conectar diretamente o estado da aplicação com a interface.

---

## Próximos passos

Existem várias melhorias que podem ser implementadas conforme avanço nos estudos de Vue.

### 1. Migrar o projeto para Vite

Em vez de carregar o Vue diretamente através de CDN, posso criar um projeto Vue utilizando **Vite**.

Isso proporcionaria um ambiente de desenvolvimento mais próximo de projetos reais e permitiria utilizar:

* Single File Components (`.vue`).
* Dependências através do npm.
* Melhor organização do projeto.
* Processo de build para produção.

### 2. Criar componentes reutilizáveis

A aplicação atual poderia ser dividida em componentes como:

```text
App.vue
├── TaskForm.vue
├── TaskList.vue
└── TaskItem.vue
```

Isso deixaria a aplicação mais organizada e facilitaria sua manutenção, além de demonstrar melhor o conceito de arquitetura baseada em componentes.

### 3. Melhorar o gerenciamento de tarefas

Algumas funcionalidades que poderiam ser adicionadas:

* Editar tarefas existentes.
* Ordenar tarefas por prioridade.
* Filtrar por status de conclusão.
* Adicionar datas de vencimento.
* Adicionar categorias.
* Limpar todas as tarefas concluídas.
* Exibir estatísticas das tarefas.

### 4. Melhorar a interface

A interface também poderia receber melhorias como:

* Design responsivo.
* Feedback visual para as ações do usuário.
* Animações e transições.
* Melhor acessibilidade.
* Dark mode.

### 5. Explorar novos conceitos do Vue

Como continuidade dos estudos, pretendo explorar:

* Vue Router.
* Pinia.
* Comunicação entre componentes.
* Composables.
* Validação de formulários.
* Integração com APIs.
* Operações assíncronas.
* Testes.

---

## Considerações finais

Este projeto foi uma etapa importante na minha jornada de aprendizado com Vue.

Apesar de ser uma aplicação pequena, ele permitiu praticar diversos conceitos fundamentais, principalmente **reatividade, propriedades computadas, watchers, lifecycle hooks, renderização dinâmica, estilização com CSS e armazenamento de dados no navegador**.

Nos próximos projetos, o objetivo será aplicar esses conceitos em aplicações maiores, com uma organização melhor dos componentes e utilizando recursos mais avançados do ecossistema Vue.
