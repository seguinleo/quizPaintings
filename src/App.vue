<script setup>
import { ref, computed } from 'vue'

const baseUrl = import.meta.env.BASE_URL

const paintings = [
  {
    id: 1,
    image: 'img/1.webp',
    title: 'Un enterrement à Ornans',
    artist: 'Gustave Courbet'
  },
  {
    id: 2,
    image: 'img/2.webp',
    title: 'Un dimanche après-midi à l\'Île de la Grande Jatte',
    artist: 'Georges Seurat'
  },
  {
    id: 3,
    image: 'img/3.webp',
    title: 'L\'Automne',
    artist: 'Giuseppe Arcimboldo'
  },
  {
    id: 4,
    image: 'img/4.webp',
    title: 'Butterfly',
    artist: 'Yayoi Kusama'
  },
  {
    id: 5,
    image: 'img/5.webp',
    title: 'Composition VII',
    artist: 'Wassily Kandinsky'
  },
  {
    id: 6,
    image: 'img/6.webp',
    title: 'Les Mangeurs de pommes de terre',
    artist: 'Vincent van Gogh'
  },
  {
    id: 7,
    image: 'img/7.webp',
    title: 'La Mort de Marat',
    artist: 'Jacques-Louis David'
  },
  {
    id: 8,
    image: 'img/8.webp',
    title: 'Le Cerf blessé',
    artist: 'Frida Kahlo'
  },
  {
    id: 9,
    image: 'img/9.webp',
    title: 'L\'Île des morts',
    artist: 'Arnold Böcklin'
  },
  {
    id: 10,
    image: 'img/10.webp',
    title: 'Le Cri',
    artist: 'Edvard Munch'
  },
  {
    id: 11,
    image: 'img/11.webp',
    title: 'Le Gentilhomme à la main sur la poitrine',
    artist: 'Le Greco'
  },
  {
    id: 12,
    image: 'img/12.webp',
    title: 'Saturne dévorant un de ses fils',
    artist: 'Francisco de Goya'
  },
  {
    id: 13,
    image: 'img/13.webp',
    title: 'D\'où venons-nous ? Que sommes-nous ? Où allons-nous ?',
    artist: 'Paul Gauguin'
  },
  {
    id: 14,
    image: 'img/14.webp',
    title: 'Judith et sa servante',
    artist: 'Artemisia Gentileschi'
  },
  {
    id: 15,
    image: 'img/15.webp',
    title: 'La Petite Fille au ballon',
    artist: 'Banksy'
  },
  {
    id: 16,
    image: 'img/16.webp',
    title: 'La Jeune Fille à la perle',
    artist: 'Johannes Vermeer'
  },
  {
    id: 17,
    image: 'img/17.webp',
    title: 'American Gothic',
    artist: 'Grant Wood'
  },
  {
    id: 18,
    image: 'img/18.webp',
    title: 'Les Raboteurs de parquet',
    artist: 'Gustave Caillebotte'
  },
  {
    id: 19,
    image: 'img/19.webp',
    title: 'La Danse',
    artist: 'Henri Matisse'
  },
  {
    id: 20,
    image: 'img/20.webp',
    title: 'La Laitière',
    artist: 'Johannes Vermeer'
  },
  {
    id: 21,
    image: 'img/21.webp',
    title: 'Nighthawks',
    artist: 'Edward Hopper'
  },
  {
    id: 22,
    image: 'img/22.webp',
    title: 'Impression, soleil levant',
    artist: 'Claude Monet'
  },
  {
    id: 23,
    image: 'img/23.webp',
    title: 'Les Glaneuses',
    artist: 'Jean-François Millet'
  },
  {
    id: 24,
    image: 'img/24.webp',
    title: 'L\'Absinthe',
    artist: 'Edgar Degas'
  },
  {
    id: 25,
    image: 'img/25.webp',
    title: 'L\'Enlèvement des Sabines',
    artist: 'Nicolas Poussin'
  },
  {
    id: 26,
    image: 'img/26.webp',
    title: 'La Classe de danse',
    artist: 'Edgar Degas'
  },
  {
    id: 27,
    image: 'img/27.webp',
    title: 'La Cène',
    artist: 'Léonard de Vinci'
  },
  {
    id: 28,
    image: 'img/28.webp',
    title: 'La Fornarina',
    artist: 'Raphaël'
  },
  {
    id: 29,
    image: 'img/29.webp',
    title: 'La Liberté guidant le peuple',
    artist: 'Eugène Delacroix'
  },
  {
    id: 30,
    image: 'img/30.webp',
    title: 'La Montagne Sainte-Victoire vue de Bellevue',
    artist: 'Paul Cézanne'
  },
  {
    id: 31,
    image: 'img/31.webp',
    title: 'La Mort de Sardanapale',
    artist: 'Eugène Delacroix'
  },
  {
    id: 32,
    image: 'img/32.webp',
    title: 'La Naissance de Vénus',
    artist: 'Sandro Botticelli'
  },
  {
    id: 33,
    image: 'img/33.webp',
    title: 'Le Printemps',
    artist: 'Sandro Botticelli'
  },
  {
    id: 34,
    image: 'img/34.webp',
    title: 'La Ronde de nuit',
    artist: 'Rembrandt'
  },
  {
    id: 35,
    image: 'img/35.webp',
    title: 'Les Ménines',
    artist: 'Diego Velázquez'
  },
  {
    id: 36,
    image: 'img/36.webp',
    title: 'Le Jugement dernier',
    artist: 'Michel-Ange'
  },
  {
    id: 37,
    image: 'img/37.webp',
    title: 'Le Berceau',
    artist: 'Berthe Morisot'
  },
  {
    id: 38,
    image: 'img/38.webp',
    title: 'Le Canigou',
    artist: 'Juan Gris'
  },
  {
    id: 39,
    image: 'img/39.webp',
    title: 'Le Déjeuner sur l\'herbe',
    artist: 'Édouard Manet'
  },
  {
    id: 40,
    image: 'img/40.webp',
    title: 'Le Désespéré',
    artist: 'Gustave Courbet'
  },
  {
    id: 41,
    image: 'img/41.webp',
    title: 'Le Jugement de Salomon',
    artist: 'Nicolas Poussin'
  },
  {
    id: 42,
    image: 'img/42.webp',
    title: 'Le Radeau de la Méduse',
    artist: 'Théodore Géricault'
  },
  {
    id: 43,
    image: 'img/43.webp',
    title: 'Le Sacre de Napoléon',
    artist: 'Jacques-Louis David'
  },
  {
    id: 44,
    image: 'img/44.webp',
    title: 'Le Serment des Horaces',
    artist: 'Jacques-Louis David'
  },
  {
    id: 45,
    image: 'img/45.webp',
    title: 'Le Verrou',
    artist: 'Jean-Honoré Fragonard'
  },
  {
    id: 46,
    image: 'img/46.webp',
    title: 'Les Demoiselles d\'Avignon',
    artist: 'Pablo Picasso (la merde)'
  },
  {
    id: 47,
    image: 'img/47.webp',
    title: 'Les Joueurs de cartes',
    artist: 'Paul Cézanne'
  },
  {
    id: 48,
    image: 'img/48.webp',
    title: 'La Trahison des images',
    artist: 'René Magritte'
  },
  {
    id: 49,
    image: 'img/49.webp',
    title: 'La Persistance de la mémoire',
    artist: 'Salvador Dalí'
  },
  {
    id: 50,
    image: 'img/50.webp',
    title: 'La Joconde',
    artist: 'Léonard de Vinci'
  },
  {
    id: 51,
    image: 'img/51.webp',
    title: 'Narcisse',
    artist: 'Le Caravage'
  },
  {
    id: 52,
    image: 'img/52.webp',
    title: 'Les Noces de Cana',
    artist: 'Paul Véronèse'
  },
  {
    id: 53,
    image: 'img/53.webp',
    title: 'Nymphéas',
    artist: 'Claude Monet'
  },
  {
    id: 54,
    image: 'img/54.webp',
    title: 'Guernica',
    artist: 'Pablo Picasso (la merde)'
  },
  {
    id: 55,
    image: 'img/55.webp',
    title: 'Le Déjeuner des canotiers',
    artist: 'Auguste Renoir'
  },
  {
    id: 56,
    image: 'img/56.webp',
    title: 'Bal du moulin de la Galette',
    artist: 'Auguste Renoir'
  },
  {
    id: 57,
    image: 'img/57.webp',
    title: 'Saint Jean-Baptiste',
    artist: 'Léonard de Vinci'
  },
  {
    id: 58,
    image: 'img/58.webp',
    title: 'Légende du marais',
    artist: 'Paul Klee'
  },
  {
    id: 59,
    image: 'img/59.webp',
    title: 'La Leçon d\'anatomie du docteur Tulp',
    artist: 'Rembrandt'
  },
  {
    id: 60,
    image: 'img/60.webp',
    title: 'Les Époux Arnolfini',
    artist: 'Jan van Eyck'
  },
  {
    id: 61,
    image: 'img/61.webp',
    title: 'Le Dernier Voyage du Téméraire',
    artist: 'J. M. W. Turner'
  },
  {
    id: 62,
    image: 'img/62.webp',
    title: 'Le Jardin des délices',
    artist: 'Jérôme Bosch'
  },
  {
    id: 63,
    image: 'img/63.webp',
    title: 'Le Baiser',
    artist: 'Gustav Klimt'
  },
  {
    id: 64,
    image: 'img/64.webp',
    title: 'L\'École d\'Athènes',
    artist: 'Raphaël'
  },
  {
    id: 65,
    image: 'img/65.webp',
    title: 'Les Hasards heureux de l\'escarpolette',
    artist: 'Jean-Honoré Fragonard'
  },
  {
    id: 66,
    image: 'img/66.webp',
    title: 'Tres de mayo',
    artist: 'Francisco de Goya'
  },
  {
    id: 67,
    image: 'img/67.webp',
    title: 'La Grande Vague de Kanagawa',
    artist: 'Hokusai'
  },
  {
    id: 68,
    image: 'img/68.webp',
    title: 'La Nuit étoilée',
    artist: 'Vincent van Gogh'
  },
  {
    id: 69,
    image: 'img/69.webp',
    title: 'Vue de Delft',
    artist: 'Johannes Vermeer'
  },
  {
    id: 70,
    image: 'img/70.webp',
    title: 'Vue de Tolède',
    artist: 'Le Greco'
  },
  {
    id: 71,
    image: 'img/71.webp',
    title: 'Les Tournesols',
    artist: 'Vincent van Gogh'
  },
  {
    id: 72,
    image: 'img/72.webp',
    title: 'Le Voyageur contemplant une mer de nuages',
    artist: 'Caspar David Friedrich'
  },
  {
    id: 73,
    image: 'img/73.webp',
    title: 'Marilyn Diptych',
    artist: 'Andy Warhol'
  },
  {
    id: 74,
    image: 'img/74.webp',
    title: 'Judith décapitant Holopherne',
    artist: 'Artemisia Gentileschi'
  },
  {
    id: 75,
    image: 'img/75.webp',
    title: 'La Création d\'Adam',
    artist: 'Michel-Ange'
  },
  {
    id: 76,
    image: 'img/76.webp',
    title: 'Olympia',
    artist: 'Édouard Manet'
  },
  {
    id: 77,
    image: 'img/77.webp',
    title: 'La Vierge et l\'Enfant entourés d\'anges (Diptyque de Melun)',
    artist: 'Jean Fouquet'
  },
  {
    id: 78,
    image: 'img/78.webp',
    title: 'Terrasse du café le soir',
    artist: 'Vincent van Gogh'
  },
  {
    id: 79,
    image: 'img/79.webp',
    title: 'La Chambre de Van Gogh à Arles',
    artist: 'Vincent van Gogh'
  },
  {
    id: 80,
    image: 'img/80.webp',
    title: 'La Dame en blanc',
    artist: 'Marie Bracquemond'
  }
]

const currentPainting = ref(null)
const quizPaintings = ref([])
const quizFinished = ref(false)
const questionType = ref(null)
const answers = ref([])
const selectedAnswer = ref(null)
const timerStarted = ref(false)
const score = ref(0)
const elapsedTime = ref(0)
const questionNumber = ref(0)
const totalQuestions = 10

function shuffle(array) {
  const result = [...array]

  for (let i = result.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1))
      ;[result[i], result[j]] = [result[j], result[i]]
  }

  return result
}

function preloadImages(paintingsToPreload) {
  paintingsToPreload.forEach((painting) => {
    const img = new Image()
    img.src = `${baseUrl}${painting.image}`
  })
}

function startQuiz() {
  stopTimer()

  const shuffledPaintings = shuffle(paintings)
  quizPaintings.value = shuffledPaintings.slice(0, totalQuestions)

  preloadImages(quizPaintings.value)

  questionNumber.value = 0
  score.value = 0
  elapsedTime.value = 0
  quizFinished.value = false
  timerStarted.value = false

  generateQuestion()
}

function generateQuestion() {
  const painting = quizPaintings.value[questionNumber.value]

  if (!painting) return

  currentPainting.value = painting
  questionType.value = Math.random() < 0.5 ? 'artist' : 'title'

  const correctAnswer =
    questionType.value === 'artist'
      ? painting.artist
      : painting.title

  const wrongAnswers = paintings
    .filter(p => p.id !== painting.id)
    .map(p =>
      questionType.value === 'artist'
        ? p.artist
        : p.title
    )
    .filter(value => value !== correctAnswer)
    .filter((value, index, array) => array.indexOf(value) === index)

  const selectedWrongAnswers = shuffle(wrongAnswers).slice(0, 3)

  answers.value = shuffle([
    correctAnswer,
    ...selectedWrongAnswers
  ])

  selectedAnswer.value = null
}

function nextQuestion() {
  if (quizFinished.value) return
  if (questionNumber.value >= totalQuestions - 1) return
  questionNumber.value++
  generateQuestion()
}

function selectAnswer(answer) {
  if (selectedAnswer.value !== null) return

  selectedAnswer.value = answer

  if (!timerStarted.value) {
    timerStarted.value = true
    startTimer()
  }

  const correctAnswer =
    questionType.value === 'artist'
      ? currentPainting.value.artist
      : currentPainting.value.title

  if (answer === correctAnswer) {
    score.value++
  }

  if (questionNumber.value === totalQuestions - 1) {
    stopTimer()
    quizFinished.value = true
  }
}

let timer = null

function startTimer() {
  stopTimer()

  timer = setInterval(() => {
    elapsedTime.value++
  }, 1000)
}

function stopTimer() {
  if (timer !== null) {
    clearInterval(timer)
    timer = null
  }
}

function formatTime(seconds) {
  const minutes = Math.floor(seconds / 60)
  const remainingSeconds = seconds % 60

  return minutes
    ? `${minutes}min ${remainingSeconds}s`
    : `${remainingSeconds}s`
}

const formattedTime = computed(() =>
  formatTime(elapsedTime.value)
)

startQuiz()
</script>

<template>
  <main>
    <header id="score">
      <div>
        <span>Score</span>
        <span>{{ score }}</span>
      </div>
      <div>
        <span>Timer</span>
        <span>{{ formattedTime }}</span>
      </div>
      <div>
        <span>Question</span>
        <span>{{ questionNumber + 1 }} / {{ totalQuestions }}</span>
      </div>
    </header>
    <section v-if="currentPainting && !quizFinished">
      <div id="top-text">
        <h1 v-if="selectedAnswer === null">
          {{
            questionType === 'artist'
              ? 'Qui a peint cette œuvre ?'
              : 'Quel est le titre de cette œuvre ?'
          }}
        </h1>
        <p v-else>
          <span class="italic">{{ currentPainting.title }}</span>, {{ currentPainting.artist }}
        </p>
      </div>
      <div class="painting">
        <img :src="`${baseUrl}${currentPainting.image}`" :alt="currentPainting.title" />
      </div>
      <div class="answers">
        <button v-for="answer in answers" :key="answer" @click="selectAnswer(answer)" :class="{
          selected: selectedAnswer === answer,
          correct:
            selectedAnswer !== null &&
            answer === (
              questionType === 'artist'
                ? currentPainting.artist
                : currentPainting.title
            ),
          wrong:
            selectedAnswer === answer &&
            answer !== (
              questionType === 'artist'
                ? currentPainting.artist
                : currentPainting.title
            )
        }">
          {{ answer }}
        </button>
      </div>
      <button v-if="selectedAnswer !== null" class="next" @click="nextQuestion">
        Question suivante
      </button>
    </section>
    <section v-if="quizFinished">
      <button class="next" @click="startQuiz">
        Rejouer
      </button>
      <div id="footer">fuck ai</div>
    </section>
  </main>
</template>
