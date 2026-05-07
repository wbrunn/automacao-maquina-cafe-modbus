from pyModbusTCP.client import ModbusClient
import time

#primeira posição: estadoBebida (1 cafe, 2 cafe com leite)
#segunda posicao: estadoAcucar (1 com açucar, 2 sem açucar)
c = ModbusClient(host="localhost", port=1502, unit_id=1, auto_open=True)

print("--- Supervisório Python Conectado ---")
leituraAnterior= [0, 0]
estoque = {"cafe": 100, "leite": 100, "agua": 500, "acucar": 50}
producao = {"cafe_puro": 0, "com_leite": 0, "sem_acucar": 0, "com_acucar": 0}
primeiro_loop = False

try:
    while True:
        if c.is_open:
            if primeiro_loop == False:
                print('Conexao estabelecida')
                primeiro_loop = True
            leituraAtual = c.read_input_registers(0, 2)
            if leituraAtual is not None and leituraAtual != leituraAnterior and leituraAtual != [0, 0]:
                if leituraAtual[0] == 1:
                    producao["cafe_puro"] += 1
                    estoque["cafe"] -= 3
                    estoque["agua"] -=5
                if leituraAtual[0] == 2:
                    producao["com_leite"] += 1
                    estoque["cafe"] -= 2
                    estoque["agua"] -=7
                    estoque["leite"] -= 3
                if leituraAtual[1] == 1:
                    producao["com_acucar"] += 1
                    estoque["acucar"] -= 2
                if leituraAtual[1] == 2:
                    producao["sem_acucar"] += 1
                print(f"{'='*30}")
                print(f"PRODUÇÃO TOTAL: {producao}")
                print(f"ESTOQUE ATUAL: {estoque}")
                print(f"{'='*30}")

            leituraAnterior = leituraAtual
            
        else:
            print("Tentando conectar...")
            primeiro_loop = False
            c.open()
            
        time.sleep(0.5)
except KeyboardInterrupt:
    print("Scanner parado.")
