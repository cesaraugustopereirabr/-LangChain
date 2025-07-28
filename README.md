# -LangChain
Automatização da criação de testes unitários utilizando modelos de linguagem com LangChain e ChatGPT.
# Python Calculation Agent

Agente simples em Python para interpretar comandos de cálculo em texto e executar expressões matemáticas usando `eval()`.

---

## Funcionalidades

- Recebe comandos no formato:  
  `Calculate 2+2 in Python`  
  `Calculate 10 / 2`
- Extrai e avalia a expressão matemática da string
- Retorna o resultado ou mensagem de erro

---

## Uso

Copie e cole o código abaixo em um arquivo Python (`agent.py`) e execute-o para testar:

```python
def agent_run(command: str):
    command = command.lower()
    if "calculate" in command:
        start = command.find("calculate") + len("calculate")
        end = command.find("in python")
        if end == -1:
            expression = command[start:].strip()
        else:
            expression = command[start:end].strip()

        try:
            result = eval(expression, {}, {})
            return str(result)
        except Exception as e:
            return f"Erro na avaliação: {e}"
    else:
        return "Comando não entendido."

if __name__ == "__main__":
    comando = "Calculate 2+2 in Python"
    resposta = agent_run(comando)
    print("Resposta do agente:", resposta)

