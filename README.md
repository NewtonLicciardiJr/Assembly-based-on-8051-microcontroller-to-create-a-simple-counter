# Contador em Assembly para 8051

## Descrição

Este repositório contém exemplos de programas em Assembly para o microcontrolador 8051, implementando um contador decimal que exibe valores em um display. É um projeto de estudo para arquitetura de computadores, demonstrando conceitos como manipulação de BCD, subrotinas, pilha e controle de displays.

O programa conta de 00 a 99 em decimal, utilizando ajuste BCD e exibindo os dígitos em displays de 7 segmentos.

## Arquivos

- `contador.A51`: Versão inicial do programa contador.
- `contador_v2.A51`: Versão 2 com possíveis melhorias ou variações.
- `contador_v3.A51`: Versão 3.
- `*.LNK`: Arquivos de link gerados pelo assembler.
- `*.LST`: Arquivos de listagem com código assembly e endereços.
- `*.p51`: Arquivos objeto ou hex gerados.

## Requisitos

- Assembler compatível com 8051, como ASEM-51 ou Keil µVision.
- Simulador 8051 (como Proteus ou simulador online) ou um kit de desenvolvimento físico para testar o programa.

## Como Compilar

1. Instale um assembler para 8051.
2. Execute o comando de compilação no arquivo .A51 desejado. Por exemplo, com ASEM-51:

   ```
   asem contador.A51
   ```

   Isso gerará os arquivos .LST e .p51.

## Como Executar

- Para simulação: Carregue o arquivo .hex (gerado a partir de .p51) em um simulador 8051 e execute.
- Para hardware: Programe o microcontrolador 8051 com o arquivo hex usando um programador apropriado.

## Funcionalidades

- **Contagem**: Incrementa o acumulador e ajusta para BCD.
- **Displays**: Subrotinas para acender dígitos menos e mais significativos.
- **Delay**: Subrotina para pausa, garantindo visibilidade no display.
- **Pilha**: Uso da pilha para salvar endereços de retorno de subrotinas.

O código inclui comentários explicativos e é intencionalmente não otimizado para fins educacionais.

## Autor

Prof. Newton Licciardi  
Contato: newton.licciardijr@gmail.com  


## Licença

Este projeto é para fins educacionais. Consulte o autor para uso comercial.
