import requests
import time

def monitor_site(url, intervalo, num_iteracoes):
    print(f"Monitorando o site {url}...")

    for i in range(num_iteracoes):
        try:
            inicio = time.time()
            resposta = requests.get(url)
            tempo_resposta = time.time() - inicio
            status = resposta.status_code
            print(f"Iteração {i+1}: Status={status}, Tempo de resposta={tempo_resposta:.2f} segundos")
        except requests.exceptions.RequestException as e:
            print(f"Iteração {i+1}: Erro - {e}")

        time.sleep(intervalo)

if __name__ == "__main__":
    url = "http://example.com"  # Substitua pela URL do site que você deseja monitorar
    intervalo = 10  # Intervalo entre cada verificação em segundos
    num_iteracoes = 5  # Número de vezes que o site será verificado

    monitor_site(url, intervalo, num_iteracoes)
