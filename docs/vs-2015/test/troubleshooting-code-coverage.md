---
title: Solução de problemas de cobertura de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bf21286143b2b9543c834f00ed31ddaa4cef63
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660370"
---
# <a name="troubleshooting-code-coverage"></a>Solução de problemas de cobertura de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A ferramenta de análise da cobertura de código no Visual Studio coleta dados para assemblies nativos e gerenciados (arquivos .dll ou .exe). No entanto, em alguns casos, a janela resultados da cobertura de código exibe um erro semelhante a "resultados vazios gerados:...." Há várias razões possíveis pelas quais isso pode acontecer. Este tópico deve ajudar a resolver esses problemas.

## <a name="what-you-should-see"></a>O que você deve ver
 Se você escolher um comando **Analisar Cobertura de Código** no menu Teste e se o build e os testes forem executados com êxito, você deverá ver uma lista de resultados na janela Cobertura de Código. Você talvez tenha que expandir os itens para ver os detalhes.

 ![Resultados da cobertura de código com cores](../test/media/codecoverage1.png "CodeCoverage1")

 Para obter mais informações, consulte [Usando cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Possíveis motivos para não ver resultados ou ver resultados anteriores

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Você tem a edição certa do Visual Studio?
 Você precisa do Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Nenhum teste foi executado
 Análise Verifique sua janela de saída. Na lista suspensa **Mostrar Saída de**, escolha **Testes**. Verifique se existe algum aviso ou erro registrado em log.

 Explicação a análise de cobertura de código é feita enquanto os testes estão em execução. Ela inclui apenas assemblies carregados na memória durante a execução dos testes. Se nenhum dos testes for executado, não haverá nada para a cobertura de código a ser reportado.

 Resolução no Gerenciador de testes, escolha **executar tudo** para verificar se os testes são executados com êxito. Corrija todas as falhas antes de usar **Analisar Cobertura de Código**.

### <a name="youre-looking-at-a-previous-result"></a>Você está observou um resultado anterior
 Quando você modificar e reexecutar os testes, um resultado anterior da cobertura de código poderá permanecer visível, inclusive a coloração de código com base nessa execução anterior.

1. Executar Analisar Cobertura de Código.

2. Não se esqueça de selecionar o conjunto de resultados mais recente na janela de resultados Cobertura de Código.

### <a name="pdb-symbol-files-are-unavailable"></a>Os arquivos .pdb (símbolo) não estão disponíveis
 A análise abre a pasta de destino de compilação (normalmente bin\Debug) e verifica se, para cada assembly, há um arquivo. pdb no mesmo diretório que o arquivo. dll ou. exe.

 Explicação o mecanismo de cobertura de código requer que cada assembly tenha seu arquivo. PDB associado acessível durante a execução de teste. Se não houver arquivo .pdb para um determinado assembly, ele não será analisado.

 O arquivo .pdb deve ser gerado com base na mesma compilação dos arquivos .dll ou .exe.

 Resolução certifique-se de que as configurações de Build gerem o arquivo. pdb. Se os arquivos .pdb não forem atualizados quando o projeto for compilado, abra as propriedades do projeto, selecione a página **Build**, escolha **Avançado** e inspecione **Informações de Depuração**.

 Se os arquivos .pdb e .dll ou .exe estiverem em locais diferentes, copie o arquivo .pdb para o mesmo diretório. Também é possível configurar o mecanismo de cobertura de código para procurar arquivos .pdb em outro local. Para obter mais informações, consulte [Personalizando a análise de cobertura de código](../test/customizing-code-coverage-analysis.md).

### <a name="using-an-instrumented-or-optimized-binary"></a>Usando um binário instrumentado ou otimizado
 A análise determina se o binário passou por qualquer forma de otimização avançada, como a otimização guiada por perfil, ou foi instrumentado por uma ferramenta de criação de perfil, como VSInstr. exe ou VSPerfMon. exe.

 Explicação se um assembly já tiver sido instrumentado ou otimizado por outra ferramenta de criação de perfil, o assembly será omitido da análise de cobertura de código.

 A análise de cobertura de código não pode ser realizada nesses assemblies.

 A resolução desliga a otimização e usa uma nova compilação.

### <a name="code-is-not-managed-net-or-native-c-code"></a>O código é não gerenciado (.NET) ou nativo (C++)
 Análise Verifique se você está executando alguns testes em código gerenciado C++ ou.

 Explicação a análise de cobertura de código no Visual Studio está disponível apenas em códigoC++gerenciado e nativo (). Se você estiver trabalhando com ferramentas de terceiros, um ou todo o código poderá ser executado em uma plataforma diferente.

 Nenhuma resolução disponível.

### <a name="assembly-has-been-installed-by-ngen"></a>O assembly foi instalado por NGen
 Análise Verifique se o assembly não está carregado a partir do cache de imagem nativa.

 Explicação por motivos de desempenho, os assemblies de imagem nativa não são analisados. Para obter mais informações, consulte [Ngen.exe (Gerador de Imagens Nativas)](https://msdn.microsoft.com/library/44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66).

 Resolução use uma versão MSIL do assembly. Não o processe com NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Arquivo .runsettings personalizado com sintaxe incorreta
 Análise se você estiver usando um arquivo. RunSettings personalizado, ele poderá conter um erro de sintaxe.

 Isso resulta na ausência de execução de cobertura de código. A janela de cobertura de código não é aberta ao final da execução de teste ou mostra resultados anteriores.

 Explicação você pode executar os testes de unidade com um arquivo. RunSettings personalizado para configurar opções de cobertura de código. As opções permitem incluir ou excluir arquivos. Para obter mais informações, consulte [Personalizando a análise de cobertura de código](../test/customizing-code-coverage-analysis.md).

 A resolução há dois tipos possíveis de falhas:

- **Erro de XML**

     Abra o arquivo .runsettings no editor XML do Visual Studio. Procure indicações de erro.

- **Erro na expressão regular**

  Cada cadeia de caracteres no arquivo é uma expressão regular. Revise cada um em busca de erros e, em especial, procure:

  - Parênteses incompatíveis (...) ou parênteses sem escape \\(…\\). Se quiser corresponder um parêntese na cadeia de pesquisa, você deverá usar o escape. Por exemplo, para realizar a correspondência de uma função, use: `.*MyFunction\(double\)`

  - Asterisco ou sinal de adição no início de uma expressão. Para comparar qualquer cadeia de caracteres, use um ponto seguido de um asterisco: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Arquivo .runsettings personalizado com exclusões incorretas
 Análise se você estiver usando um arquivo. RunSettings personalizado, certifique-se de que ele inclui o assembly.

 Explicação você pode executar os testes de unidade com um arquivo. RunSettings personalizado para configurar opções de cobertura de código. As opções permitem incluir ou excluir arquivos. Para obter mais informações, consulte [Personalizando a análise de cobertura de código](../test/customizing-code-coverage-analysis.md).

 Resolução remova todos os nós de `Include` do arquivo. RunSettings e, em seguida, remova todos os nós de `Exclude`. Se isso corrigir o problema, recoloque-os em estágios.

 Verifique se o nó DataCollectors especifica a Cobertura de Código. Compare-o com o exemplo em [Personalizando a análise de cobertura de código](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Um código é sempre mostrado como não coberto

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>O código de inicialização em DLLs nativas é executado antes da instrumentação
 A análise no código nativo vinculado estaticamente, parte da função de inicialização **DllMain** e do código que ela chama é às vezes mostrada como não coberta, embora o código tenha sido executado.

 Explicação a ferramenta de cobertura de código funciona inserindo a instrumentação em um assembly logo antes de o aplicativo começar a ser executado. Em qualquer assembly carregado anteriormente, o código de inicialização em **DllMain** é executado assim que o assembly é carregado e antes da execução do aplicativo. Esse código aparentemente não estará coberto.

 Normalmente, isso se aplica aos assemblies carregados estaticamente.

 Resolução nenhum.

## <a name="see-also"></a>Consulte também
 [Usando cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
