---
title: O processo de transformação de modelo de texto
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 518c06f8630ad9fa7742f7b3e85ac27263cd0a86
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605803"
---
# <a name="the-text-template-transformation-process"></a>O processo de transformação de modelo de texto
O processo de transformação de modelo de texto usa um arquivo de modelo de texto como entrada e gera um novo arquivo de texto como a saída. Por exemplo, você pode usar modelos de texto para gerar Visual Basic C# ou código, ou pode gerar um relatório HTML.

 Três componentes fazem parte desse processo: o mecanismo, o host e os processadores de diretiva. O mecanismo controla o processo; Ele interage com o host e com o processador de diretiva para produzir o arquivo de saída. O host fornece qualquer interação com o ambiente, como localizar arquivos e assemblies. O processador de diretivas adiciona funcionalidade, como a leitura de dados de um arquivo XML ou de um banco de dados.

 O processo de transformação de modelo de texto é executado em duas etapas. Primeiro, o mecanismo cria uma classe temporária, que é conhecida como a classe de transformação gerada. Essa classe contém o código que é gerado pelas diretivas e blocos de controle. Depois disso, o mecanismo compila e executa a classe de transformação gerada para produzir o arquivo de saída.

## <a name="components"></a>Componentes

|Componente|Descrição|Personalizável (Sim/não)|
|-|-|-|
|Motores|O componente do mecanismo controla o processo de transformação do modelo de texto|Nº|
|Host|O host é a interface entre o mecanismo do e o ambiente do usuário. O Visual Studio é um host do processo de transformação de texto.|Sim. Você pode escrever um host personalizado.|
|Processadores de diretiva|Os processadores de diretiva são classes que manipulam diretivas em modelos de texto. Você pode usar diretivas para fornecer dados a um modelo de texto de uma fonte de entrada.|Sim. Você pode escrever processadores de diretiva personalizada|

## <a name="the-engine"></a>O mecanismo do
 O mecanismo recebe o modelo como uma cadeia de caracteres do host, que manipula todos os arquivos que são usados no processo de transformação. Em seguida, o mecanismo solicita que o host Localize qualquer processador de diretiva personalizada e outros aspectos do ambiente. Em seguida, o mecanismo compila e executa a classe de transformação gerada. O mecanismo retorna o texto gerado para o host, que normalmente salva o texto em um arquivo.

## <a name="the-host"></a>O host
 O host é responsável por qualquer coisa relacionada ao ambiente fora do processo de transformação, incluindo o seguinte:

- Localizando texto e arquivos binários solicitados pelo mecanismo ou um processador de diretivas. O host pode pesquisar diretórios e o cache de assembly global para localizar assemblies. O host pode localizar o código do processador de diretivas personalizado para o mecanismo. O host também pode localizar e ler arquivos de texto e retornar seu conteúdo como cadeias de caracteres.

- Fornecendo listas de assemblies e namespaces padrão que são usados pelo mecanismo para criar a classe de transformação gerada.

- Fornecer o domínio do aplicativo que é usado quando o mecanismo compila e executa a classe de transformação gerada. Um domínio de aplicativo separado é usado para proteger o aplicativo host contra erros no código do modelo.

- Gravando o arquivo de saída gerado.

- Definindo a extensão padrão para o arquivo de saída gerado.

- Manipulando erros de transformação de modelo de texto. Por exemplo, o host pode exibir os erros na interface do usuário ou gravá-los em um arquivo. (No Visual Studio, os erros são exibidos na janela de mensagem de erro.)

- Fornecer um valor de parâmetro necessário se um usuário tiver chamado uma diretiva sem fornecer um valor. O processador de diretiva pode especificar o nome da diretiva e o parâmetro e solicitar que o host forneça um valor padrão, se tiver um.

## <a name="directives-and-directive-processors"></a>Diretivas e processadores de diretiva
 Uma diretiva é um comando em seu modelo de texto. Ele fornece parâmetros para o processo de geração. Normalmente, as diretivas definem a origem e o tipo do modelo ou outra entrada e a extensão de nome de arquivo do arquivo de saída.

 Um processador de diretiva pode processar uma ou mais diretivas. Ao transformar um modelo, você deve ter instalado um processador de diretiva que pode lidar com as diretivas em seu modelo.

 As diretivas funcionam adicionando o código na classe de transformação gerada. Você chama as diretivas de um modelo de texto e o mecanismo processa todas as chamadas de diretiva ao criar a classe de transformação gerada. Depois de chamar uma diretiva com êxito, o restante do código que você escreve em seu modelo de texto pode contar com a funcionalidade que a diretiva fornece. Por exemplo, você pode fazer a seguinte chamada para a diretiva `import` em seu modelo:

 `<#@ import namespace="System.Text" #>`

 O processador de diretiva padrão converte isso em uma instrução `using` na classe de transformação gerada. Em seguida, você pode usar a classe `StringBuilder` no restante do código do modelo sem qualificá-la como `System.Text.StringBuilder`.