# batalha-

const Tamanho_Tabuleiro = 5;
const Quant_Barco = 3;
let Tabuleiro = [];
let Tentativas = 0;
let Acertos = 0;


for(let i = 0; i < Tamanho_Tabuleiro; i++){
    Tabuleiro[i] = [];
    for (let j = 0; j < Tamanho_Tabuleiro; j++){
         Tabuleiro[i][j] = false;
    }
}


for(let i = 0; i < Quant_Barco; i++){
    let posX, posY;
    do {
        posX = Math.floor(Math.random() * Tamanho_Tabuleiro);
        posY = Math.floor(Math.random() * Tamanho_Tabuleiro);
    } while (Tabuleiro[posX][posY]); 
    Tabuleiro[posX][posY] = true;
}


function exibeTabuleiro() {
    for (let i = 0; i < Tamanho_Tabuleiro; i++) {
        let linha = '';
        for (let j = 0; j < Tamanho_Tabuleiro; j++) {
            linha += Tabuleiro[i][j] ? 'B ' : '~ ';
        }
        console.log(linha);
    }
}


function atacar(posX, posY) {
    Tentativas++;
    if (Tabuleiro[posX][posY]) {
        Acertos++;
        console.log(`Acertou um barco em (${posX}, ${posY})!`);
        Tabuleiro[posX][posY] = false;
    } else {
        console.log(`Errou em (${posX}, ${posY}).`);
    }
}


function verificaFimDeJogo() {
    if (Acertos === Quant_Barco) {
        console.log(`Você venceu o jogo em ${Tentativas} tentativas!`);
        return true;
    }
    return false;
}


exibeTabuleiro(); 
atacar(1, 1); 
if (verificaFimDeJogo()) {
    console.log('Fim do jogo!');
}
