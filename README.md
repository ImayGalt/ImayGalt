dados const = {
  nome: 'Cláudio',
  jogador: 'Ryan',
  ocupação: 'Caçador',
  idade: 21,
  sexo: 'masculino',
  naturalidade: 'São Paulo',
  residência: 'São Paulo',

  vida: {
    atual: 12,
    máximo: 12,
  },
  sanidade: {
    atual: 62,
    máx.: 62,
  },

  armas: [
    {
      nome: 'Balestra',
      tipo: 'Arco',
      dano: '1d20',
      numCurrent: 1,
      numMax: 1,
      ataque: 5,
      alcance: '10 m',
      defeito: 1,
      área: '',
    },
    {
      nome: 'Canivete',
      tipo: 'Briga',
      dano: '1d10',
      numCurrent: '',
      numMax: '',
      ataque: '1/2',
      alcançar: '',
      defeito: 1,
      área: '',
    },
  ],
  atributos: [
    {
      tipo: 'Aparência',
      quantidade: 10,
    },
    {
      tipo: 'Constituição',
      quantidade: 10,
    },
    {
      tipo: 'Destreza',
      quantidade: 10,
    },
    {
      tipo: 'Educação',
      quantidade: 10,
    },
    {
      tipo: 'Força',
      quantidade: 10,
    },
    {
      tipo: 'Inteligência',
      quantidade: 10,
    },
    {
      tipo: 'Poder',
      quantidade: 10,
    },
    {
      tipo: 'Ordenar',
      quantidade: 10,
    },
    {
      tipo: 'Movimento',
      quantidade: 10,
    },
    {
      modelo: '?',
      quantidade: 10,
    },
  ],
}

data.weapons.map((arma, índice) => {
  addWeaponToTable(arma, índice)
})

data.attributes.map((atributo, índice) => {
  addAttribute(atributo, índice)
})

$('#nome').val(dados.nome)
$('#jogador').val(dados.jogador)
$('#ocupação').val(data.ocupação)
$('#idade').val(dados.idade)
$('#sexo').val(dados.sexo)
$('#localnascimento').val(dados.localnascimento)
$('#residência').val(dados.residência)

$('.lifeBar').css('width', `${calculateBar(data.life.current, data.life.max)}%`)
$('#lifeCount').text(`${data.life.current}/${data.life.max}`)
$('#lifeCurrent').val(data.life.current)
$('#lifeMax').val(data.life.max)

$('.sanityBar').css(
  'largura',
  `${calculateBar(data.sanity.current, data.sanity.max)}%`
)
$('#sanityCount').text(`${data.sanity.current}/${data.sanity.max}`)
$('#sanityCurrent').val(data.sanity.current)
$('#sanityMax').val(data.sanity.max)

const diceModal = $('#diceAttributes')
const vidaModal = $('#vidaModal')
const sanityModal = $('#sanityModal')

$(janela).click(função (evento) {
  if (event.target.id == 'diceAttributes') {
    diceModal.css('exibir', 'nenhum')
    $('#diceNumber').text('')
    $('#diceType').text('')

    $('.modalDice').css('transform', 'rotate(0deg)')
    $('.modalDice').css('-webkit-transform', 'rotate(0deg)')
  } else if (event.target.id == 'lifeModal') {
    lifeModal.css('exibir', 'nenhum')
  } else if (event.target.id == 'sanityModal') {
    sanityModal.css('exibir', 'nenhum')
  } else if (event.target.id == 'addWeaponModal') {
    closeModal('#addWeaponModal')
  }
})

function rollAtribute(atributo, quantidade) {
  console.log(este)

  diceModal.css('exibir', 'bloquear')

  setTimeout(() => {
    $('.modalDice').css('transform', 'rotate(360deg)')
    $('.modalDice').css('-webkit-transform', 'rotate(360deg)')
  }, 1000)

  setTimeout(() => {
    const númeroDados = rollDados('1d20')
    const diceType = calcDice(quantia, diceNumber)
    $('#diceNumber').text(diceNumber)
    $('#diceType').text(diceType)

    setTimeout(() => {
      diceModal.css('exibir', 'nenhum')
      $('#diceNumber').text('')
      $('#diceType').text('')

      $('.modalDice').css('transform', 'rotate(0deg)')
      $('.modalDice').css('-webkit-transform', 'rotate(0deg)')
    }, 20000)
  }, 2000)
}

$('.lifeBar').click(function () {
  console.log(este)
  lifeModal.css('exibir', 'bloquear')
})

$('.sanityBar').click(function () {
  console.log(este)
  sanityModal.css('exibir', 'bloquear')
})

$('#addWeapon').click(function () {
  openModal('#addWeaponModal')
})

$('#lesão').change(function () {
  if (este.marcado) {
    console.log('Modo lesão grave ativado!')
  } senão {
    console.log('Modo lesão grave desativado!')
  }
})

$('#lesão').change(function () {
  if (este.marcado) {
    console.log('Modo lesão ativado!')
  } senão {
    console.log('Modo lesionado desativado!')
  }
})

$('#morrendo').change(function () {
  if (este.marcado) {
    console.log('Modo morrendo ativado!')
  } senão {
    console.log('Modo morrendo desativado!')
  }
})

$('#traumatizado').change(function () {
  if (este.marcado) {
    console.log('Modo traumatizado ativado!')
  } senão {
    console.log('Modo traumatizado desativado!')
  }
})

$('#crazed').change(function () {
  if (este.marcado) {
    console.log('Modo enlouquecido ativado!')
  } senão {
    console.log('Modo enlouquecido desativado!')
  }
})

$('#addWeaponForm').submit(function (event) {
  var tipo de arma = ''

  if ($('#weaponType').val() == 'disparar') {
    tipo de arma = 'Fogo'
  } else if ($('#weaponType').val() == 'arch') {
    tipo de arma = 'Arco'
  } else if ($('#weaponType').val() == 'lutar') {
    tipo de arma = 'Briga'
  }

  arma const = {
    nome: $('#weaponName').val(),
    tipo: tipo de arma,
    dano: $('#weapondamage').val(),
    numCurrent: $('#weaponNumCurrent').val(),
    numMax: $('#weaponNumMax').val(),
    ataque: $('#weaponAttack').val(),
    alcance: $('#weaponReach').val(),
    defeito: $('#weaponDefect').val(),
    area: $('#weaponArea').val(),
  }

  data.weapons.push(arma)
  const id = data.weapons.length - 1
  addWeaponToTable(arma, id)

  closeModal('#addWeaponModal')
  event.preventDefault()
})

$('#changeLife').submit(function (event) {
  let current = Number($('#lifeCurrent').val())
  const max = Number($('#lifeMax').val())

  if (atual > max) {
    alert('A vida atual não pode ser maior que a maxima!')
    atual = máximo
  }

  data.life.current = atual
  data.life.max = max
  $('.lifeBar').css('width', `${calculateBar(current, max)}%`)
  $('#lifeCount').text(`${current}/${max}`)

  closeModal('#vidaModal')
  event.preventDefault()
})

$('#changeSanity').submit(função (evento) {
  let current = Number($('#sanityCurrent').val())
  const max = Number($('#sanityMax').val())

  if (atual > max) {
    alert('A sanidade atual não pode ser maior que a maxima!')
    atual = máximo
  }

  data.sanity.current = atual
  data.sanity.max = max
  $('.sanityBar').css('width', `${calculateBar(current, max)}%`)
  $('#sanityCount').text(`${current}/${max}`)

  closeModal('#sanityModal')
  event.preventDefault()
})

função calcularBar(atual, max) {
  if (atual > max) {
    retornar 100
  } else if (atual < 0) {
    retornar 0
  } senão {
    valor const = (100 / max) * atual
    const string = value.toString().split('.')[0]
    porcentagem const = Number(string)
    porcentagem de retorno
  }
}

function calcDice(habilidade, dado) {
  // Não encontrei uma forma mais fácil, então fiz assim

  tabela const = [
    { normal: 20 },
    { normal: 19, bom: 20 },
    { normal: 18, bom: 20 },
    { normal: 17, bom: 19 },
    { normal: 16, bom: 19, extremo: 20 },
    { normal: 15, bom: 18, extremo: 20 },
    { normal: 14, bom: 18, extremo: 20 },
    { normal: 13, bom: 17, extremo: 20 },
    { normal: 12, bom: 17, extremo: 20 },
    { normal: 11, bom: 16, extremo: 20 },
    { normal: 10, bom: 16, extremo: 19 },
    { normal: 9, bom: 16, extremo: 19 },
    { normal: 8, bom: 15, extremo: 19 },
    { normal: 7, bom: 14, extremo: 19 },
    { normal: 6, bom: 14, extremo: 18 },
    { normal: 5, bom: 13, extremo: 18 },
    { normal: 4, bom: 13, extremo: 18 },
    { normal: 3, bom: 12, extremo: 18 },
    { normal: 2, bom: 12, extremo: 18 },
    { normal: 1, bom: 11, extremo: 17 },
  ]

  tipo const = tabela[capacidade - 1]

  if (tipo.extremo) {
    if (dado >= type.extreme) return 'Extremo'
    if (dado >= type.good) return 'Sucesso Bom'
    if (dice >= type.normal) return 'Sucesso Normal'
    if (dado <= type.normal) return 'Fracasso'
  } else if (tipo.bom) {
    if (dado >= type.good) return 'Sucesso Bom'
    if (dice >= type.normal) return 'Sucesso Normal'
    if (dado <= type.normal) return 'Fracasso'
  } else if (tipo.normal) {
    if (dice >= type.normal) return 'Sucesso Normal'
    if (dado <= type.normal) return 'Fracasso'
  }
}

function rolarDados(dados) {
  let [count, max] = dice.split('d')

  if (Número(contagem) && Número(máximo)) {
    contagem = número(contagem)
    máx = Número(máx)

    deixe total = 0

    for (deixe i = 0; i < contagem; i++) {
      total += Math.floor(Math.random() * max + 1)
    }

    retorno total
  } senão {
    retornar nulo
  }
}

function openModal(modal) {
  const Modal = $(modal)
  Modal.css('exibir', 'bloquear')
}

função fecharModal(modal) {
  const Modal = $(modal)
  Modal.css('exibir', 'nenhum')
}

function addWeaponToTable(arma, id) {
  const novaArma = $(`<tr id="weapon_${id}">
        <td>
            <button onclick="deleteWeapon(${id})">
                <i class="fa fa-trash-o lixeira"></i>
            </button>
            ${weapon.name}
        </td>
        <td>${weapon.type}</td>
        <td>${weapon.damage}</td>
        <td>${weapon.numCurrent}</td>
        <td>${weapon.numMax}</td>
        <td>${weapon.attack}</td>
        <td>${weapon.reach}</td>
        <td>${weapon.defect}</td>
        <td>${weapon.area}</td>
    </tr>`)
  $('tabela#armas').append(novaArma)
}

function addAttribute(atributo, id) {
  const newAttribute = $(`<div class="attribute" id="attribute_${id}">
    <a onclick="rollAtribute('${attribute.type}', ${attribute.amount})">
      <img class="attributeDice" src="./img/dado.png" alt="Dado">
    </a>
    <h3>${attribute.type}</h3>
    <input type="text" name="appearance" value="${attribute.amount}" id="attribute_input_${id}" desativado>
  </div>`)
  $('#attributesList').append(newAttribute)
}

function deleteWeapon(id) {
  $(`tr#${id}`).remove()
}
