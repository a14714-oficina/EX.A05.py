<h1>OBJETIVO<h1>


Desenvolver um programa em Python que permita recolher respostas a um questionário de satisfação e exportar os resultados para um ficheiro de texto, utilizando funções para organizar o código.

<h1>PROBLEMA<h1>
Uma escola deseja recolher a opinião de alunos sobre a qualidade dos serviços oferecidos (infraestruturas, atendimento, equipamentos, etc.). Pretende-se criar um programa que automatize a recolha destas respostas e armazene os resultados num ficheiro para análise futura.

<h1>CÓDIGO</h1>
[ Função para apresentar o questionário e recolher respostas ]
def apresentar_questionario():
    print("Questionário de Satisfação")
    print("Por favor, responda às seguintes perguntas:")
    
    perguntas = [
        "1. Como avalia a infraestrutura da escola? (1-5)",
        "2. Como avalia a qualidade do atendimento? (1-5)",
        "3. Como avalia os equipamentos disponíveis? (1-5)",
        "4. Está satisfeito com a limpeza das instalações? (1-5)",
        "5. Recomenda esta escola a outras pessoas? (Sim/Não)"
    ]
    
    respostas = []
    for pergunta in perguntas:
        resposta = input(pergunta + " ")
        respostas.append(resposta)
    
    return respostas


[ Função para exportar os resultados para um ficheiro ]
def exportar_resultados(respostas):
    nome_ficheiro = input("Introduza o nome do ficheiro para guardar os resultados (ex: resultados.txt): ")
    try:
        with open(nome_ficheiro, "w") as ficheiro:
            ficheiro.write("Respostas ao Questionário de Satisfação\n")
            ficheiro.write("-" * 40 + "\n")
            perguntas = [
                "1. Avaliação da infraestrutura: ",
                "2. Avaliação do atendimento: ",
                "3. Avaliação dos equipamentos: ",
                "4. Satisfação com a limpeza: ",
                "5. Recomendação: "
            ]
            for pergunta, resposta in zip(perguntas, respostas):
                ficheiro.write(pergunta + resposta + "\n")
        print(f"Resultados guardados com sucesso no ficheiro '{nome_ficheiro}'.")
    except Exception as e:
        print(f"Erro ao guardar o ficheiro: {e}")


[ Função principal para gerir o fluxo do programa ]
def main():
    while True:
        print("\nSistema de Questionário de Satisfação")
        print("1. Responder ao Questionário")
        print("2. Sair")
        opcao = input("Escolha uma opção: ")
        
        if opcao == "1":
            respostas = apresentar_questionario()
            exportar_resultados(respostas)
        elif opcao == "2":
            print("Obrigado por usar o sistema!")
            break
        else:
            print("Opção inválida! Tente novamente.")

if __name__ == "__main__":
    main()

