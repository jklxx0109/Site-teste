<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bem-vindo</title>
</head>
<body>
    <h1>Qual é o seu nome?</h1>
    <input type="text" id="nome" placeholder="Digite seu nome aqui...">
    <br><br>
    <button onclick="exibirBoasVindas()">Enviar</button>

    <p id="boas-vindas"></p>

    <div id="form-data-nascimento" style="display:none;">
        <h2>Informe sua data de nascimento:</h2>
        <input type="date" id="data-nascimento">
        <br><br>
        <button onclick="calcularIdade()">Calcular Idade</button>
        <p id="idade"></p>
    </div>

    <h2>Calculadora Simples</h2>
    <form id="calculadora">
        <label for="num1">Número 1:</label>
        <input type="number" id="num1" required><br><br>

        <label for="num2">Número 2:</label>
        <input type="number" id="num2" required><br><br>

        <label for="operacao">Operação:</label>
        <select id="operacao">
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
        </select><br><br>

        <button type="button" onclick="calcular()">Calcular</button>
    </form>

    <p id="resultado"></p>

    <script>
        function exibirBoasVindas() {
            var nome = document.getElementById("nome").value;
            document.getElementById("boas-vindas").innerText = "Olá, " + nome + "!";
            document.getElementById("form-data-nascimento").style.display = "block";
        }

        function calcularIdade() {
            var dataNascimento = document.getElementById("data-nascimento").value;
            if (dataNascimento) {
                var hoje = new Date();
                var nascimento = new Date(dataNascimento);
                var idade = hoje.getFullYear() - nascimento.getFullYear();
                var mes = hoje.getMonth() - nascimento.getMonth();

                if (mes < 0 || (mes === 0 && hoje.getDate() < nascimento.getDate())) {
                    idade--;
                }

                document.getElementById("idade").innerText = "Sua idade é: " + idade + " anos.";
            }
        }

        function calcular() {
            var num1 = parseFloat(document.getElementById("num1").value);
            var num2 = parseFloat(document.getElementById("num2").value);
            var operacao = document.getElementById("operacao").value;
            var resultado = 0;
            var erro = '';

            if (isNaN(num1) || isNaN(num2)) {
                erro = 'Por favor, insira números válidos.';
            } else {
                if (operacao === 'soma') {
                    resultado = num1 + num2;
                } else if (operacao === 'subtracao') {
                    resultado = num1 - num2;
                } else if (operacao === 'multiplicacao') {
                    resultado = num1 * num2;
                } else if (operacao === 'divisao') {
                    if (num2 !== 0) {
                        resultado = num1 / num2;
                    } else {
                        erro = 'Erro: Não é possível dividir por zero.';
                    }
                }
            }

            if (erro) {
                document.getElementById("resultado").innerText = erro;
            } else {
                document.getElementById("resultado").innerText = 'Resultado: ' + resultado;
            }
        }
    </script>
</body>
</html>
