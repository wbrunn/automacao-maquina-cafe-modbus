Automação de Máquina de Café - CODESYS & Python

Este projeto demonstra a integração entre um sistema de controle industrial e um sistema de supervisão utilizando o protocolo Modbus TCP.

Funcionalidades
- Lógica Ladder: Implementação de uma máquina de estados para o processo de venda de bebidas com café. O cliente seleciona um tipo de bebida específica e o CLP faz toda
a lógica através da linguagem Ladder para abrir e fechar válvulas, ler sensores e entregar a bebida. Abaixo, um trecho da implementação da lógioca em Ladder, responsável por gerenciar os ciclos de preparo:
![Lógica Ladder - Máquina de Estados](screenshots/screenshot_maquina_cafe.png)

- Integração Modbus: O CODESYS atua como servidor Modbus TCP, disponibilizando dados de sensores e status do processo. Para a comunicação com o supervisório em Python, as variáveis de estado foram mapeadas nos registradores conforme a imagem abaixo:
![Mapeamento de Variáveis Modbus](screenshots/screenshot_modbus_tcp.png)

- Supervisório em Python: Script que lê os registradores do CLP e exibe o status em tempo real. Além disso, atualiza uma lista contendo os valores dos insumos disponíveis no estoque e os mostra no display.

Tecnologias
- CODESYS V3.5 (SoftPLC)
- Python 3 (Biblioteca pyModbusTCP)
- Protocolo Modbus TCP

---
*Projeto desenvolvido para consolidar conhecimentos em redes industriais e programação de CLPs.*
