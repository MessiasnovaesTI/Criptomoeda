# Criptomoeda
Criando a minha Primeira Criptomoeda da Rede Ethereum

Aqui está um exemplo básico de um contrato inteligente em Solidity que cria uma criptomoeda seguindo o padrão ERC-20 na rede Ethereum. O código inclui as principais funcionalidades do padrão ERC-20, como transferência de tokens, aprovação e verificação do saldo.

solidity
Copiar código
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is ERC20, Ownable {
    constructor(uint256 initialSupply) ERC20("MyToken", "MTK") {
        _mint(msg.sender, initialSupply * (10 ** uint256(decimals())));
    }
    
    // Override the decimals function to return a custom number of decimal places
    function decimals() public view virtual override returns (uint8) {
        return 18; // You can adjust this if needed
    }
}
Explicação do Código:
Licença e Versão do Compilador:

// SPDX-License-Identifier: MIT é uma licença comum para contratos inteligentes.
pragma solidity ^0.8.0; define a versão do compilador Solidity.
Importação das Bibliotecas:

import "@openzeppelin/contracts/token/ERC20/ERC20.sol"; importa o contrato base do ERC-20 da biblioteca OpenZeppelin.
import "@openzeppelin/contracts/access/Ownable.sol"; importa o contrato Ownable, que permite que apenas o proprietário do contrato execute certas funções.
Definição do Contrato:

contract MyToken is ERC20, Ownable define um novo contrato chamado MyToken que herda das implementações de ERC20 e Ownable.
Construtor:

constructor(uint256 initialSupply) ERC20("MyToken", "MTK") define o nome do token como "MyToken" e o símbolo como "MTK".
_mint(msg.sender, initialSupply * (10 ** uint256(decimals()))); cria a quantidade inicial de tokens e atribui ao endereço que implanta o contrato. A multiplicação por 10 ** uint256(decimals()) é para considerar a precisão decimal.
Função Decimals:

function decimals() public view virtual override returns (uint8) permite definir o número de casas decimais para o token. O padrão é 18, mas você pode ajustar conforme necessário.
Compilação e Implantação:
Para compilar e implantar esse contrato, você pode usar uma ferramenta como o Remix IDE ou trufar com Hardhat/Truffle:

Usando Remix IDE:

Cole o código no Remix.
Compile o contrato.
Implante o contrato usando a interface do Remix.
Usando Hardhat/Truffle:

Instale Hardhat ou Truffle.
Crie um projeto e coloque o contrato no diretório de contratos.
Compile e implante o contrato usando scripts de migração fornecidos.
Este é um exemplo básico. Em um projeto real, você pode querer adicionar funcionalidades adicionais, como eventos ou mecanismos de governança.
