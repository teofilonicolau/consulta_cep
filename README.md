# Consulta de Endereço via CEP

Este projeto é uma aplicação simples de consulta de endereço a partir de um CEP usando a **API ViaCEP**. O usuário insere o CEP, e a aplicação retorna o endereço correspondente, incluindo rua, bairro, cidade e estado.

## Tecnologias Utilizadas

- **HTML5**: Estrutura do conteúdo.
- **CSS3**: Estilização básica da página.
- **Bootstrap 5**: Framework CSS para facilitar o layout responsivo.
- **JavaScript**: Manipulação do DOM e consumo da API ViaCEP.
- **API ViaCEP**: Para obter os dados do endereço a partir do CEP.

## Funcionalidades

- Permite ao usuário inserir um CEP para consulta.
- Ao clicar no botão "Pesquisar", a aplicação busca o endereço correspondente ao CEP digitado.
- Se o CEP for válido, os campos de endereço, bairro, cidade e estado são preenchidos automaticamente.
- Exibe uma mensagem de erro caso o CEP seja inválido ou não encontrado.

## Estrutura do Código

### 1. **HTML**
O código HTML define a estrutura básica da página, incluindo um campo para digitar o CEP e exibir as informações do endereço. Há também um botão para iniciar a consulta.

```html
<input type="text" class="form-control" id="cep" placeholder="CEP">
<button class="btn btn-primary" onclick="getAddress(document.getElementById('cep').value)">Pesquisar</button>
```
- Os outros campos (endereco, bairro, cidade, uf) são campos de entrada que estão marcados como somente leitura (readonly), pois o usuário não pode editá-los diretamente. Eles são preenchidos automaticamente com os dados da API.

- 
Aqui está um exemplo de como você pode estruturar o README em Markdown explicando o código de consulta de CEP:

markdown
Copiar código
# Consulta de Endereço via CEP

Este projeto é uma aplicação simples de consulta de endereço a partir de um CEP usando a **API ViaCEP**. O usuário insere o CEP, e a aplicação retorna o endereço correspondente, incluindo rua, bairro, cidade e estado.

## Tecnologias Utilizadas

- **HTML5**: Estrutura do conteúdo.
- **CSS3**: Estilização básica da página.
- **Bootstrap 5**: Framework CSS para facilitar o layout responsivo.
- **JavaScript**: Manipulação do DOM e consumo da API ViaCEP.
- **API ViaCEP**: Para obter os dados do endereço a partir do CEP.

## Funcionalidades

- Permite ao usuário inserir um CEP para consulta.
- Ao clicar no botão "Pesquisar", a aplicação busca o endereço correspondente ao CEP digitado.
- Se o CEP for válido, os campos de endereço, bairro, cidade e estado são preenchidos automaticamente.
- Exibe uma mensagem de erro caso o CEP seja inválido ou não encontrado.

## Estrutura do Código

### 1. **HTML**
O código HTML define a estrutura básica da página, incluindo um campo para digitar o CEP e exibir as informações do endereço. Há também um botão para iniciar a consulta.

```html
<input type="text" class="form-control" id="cep" placeholder="CEP">
<button class="btn btn-primary" onclick="getAddress(document.getElementById('cep').value)">Pesquisar</button>
Os outros campos (endereco, bairro, cidade, uf) são campos de entrada que estão marcados como somente leitura (readonly), pois o usuário não pode editá-los diretamente. Eles são preenchidos automaticamente com os dados da API.
  ```
### 2. CSS (Estilos)

 - No código CSS, foram aplicadas algumas regras básicas de estilo para melhorar a aparência da página, como uma cor de fundo clara e bordas arredondadas nos campos de entrada.
   
### 3. JavaScript

- O JavaScript é responsável por realizar a consulta à API ViaCEP e manipular o DOM para atualizar os campos da página com o endereço consultado.

 ### Função getAddress()
   - Esta função é chamada quando o usuário insere um CEP e clica no botão "Pesquisar". Ela utiliza a função fetch() para buscar os dados do endereço na API ViaCEP. Se o CEP for válido, os dados são exibidos. Caso contrário, uma mensagem de erro é exibida.
 ```JavaScript
    function getAddress(cep) {
    cep = cep.replace(/\D/g, ''); // Remove qualquer caractere nao numerico
    if (cep.length === 8) { // Valida se o CEP tem 8 digitos
        const url = `https://viacep.com.br/ws/${cep}/json/`;
        fetch(url)
            .then(response => response.json())
            .then(data => {
                if (data.erro) {
                    document.getElementById('error-message').textContent = 'CEP não encontrado.';
                    clearFields(); // Limpa os campos caso o CEP seja inválido
                } else {
                    document.getElementById('endereco').value = data.logradouro;
                    document.getElementById('bairro').value = data.bairro;
                    document.getElementById('cidade').value = data.localidade;
                    document.getElementById('uf').value = data.uf;
                    document.getElementById('error-message').textContent = '';
                }
            })
            .catch(() => {
                document.getElementById('error-message').textContent = 'Erro ao buscar o CEP.';
                clearFields();
            });
    } else {
        document.getElementById('error-message').textContent = 'CEP inválido.';
        clearFields();
    }
}

 ```

### Função clearFields()
 - Esta função é chamada para limpar os campos de endereço se o CEP for inválido ou não for encontrado.
    ```JavaScript
      function clearFields() {
    document.getElementById('endereco').value = '';
    document.getElementById('bairro').value = '';
    document.getElementById('cidade').value = '';
    document.getElementById('uf').value = '';
}
  

## 4. Bootstrap
- O framework Bootstrap foi utilizado para melhorar a responsividade da aplicação e facilitar o layout, permitindo que o design seja amigável em dispositivos móveis.

## 5. API ViaCEP
- A aplicação faz uso da API ViaCEP para obter as informações de endereço a partir do CEP. A URL da API utilizada no projeto é:

  ```
    https://viacep.com.br/ws/{CEP}/json/
  
 ## Como Executar o Projeto
  - Clone este repositório para a sua máquina.
   - Abra o arquivo index.html no navegador.
   - Digite um CEP no campo apropriado e clique em "Pesquisar".
   - O endereço correspondente ao CEP será exibido, caso seja válido.
     ![image](https://github.com/user-attachments/assets/906d7cd9-0311-42fe-bc41-486d9acf9cf4)


