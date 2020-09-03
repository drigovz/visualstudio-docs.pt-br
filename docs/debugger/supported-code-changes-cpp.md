---
title: Alterações de código com suporte (C++) | Microsoft Docs
ms.date: 02/18/2020
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: af6c0d88dd230bee768641905e200f1f47749d77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77629580"
---
# <a name="supported-code-changes-c"></a>Alterações de código suportadas (C++)
Editar e continuar para projetos C++ lida com a maioria dos tipos de alterações de código. Porém, algumas alterações não podem ser aplicadas durante a execução do programa. Para aplicar essas alterações sem suporte, você deverá parar a execução e criar uma versão atualizada do código.

 Consulte [Editar e continuar (C++)](../debugger/edit-and-continue-visual-cpp.md) para obter informações sobre como trabalhar com editar e continuar para C++ no Visual Studio.

## <a name="requirements"></a><a name="BKMK_Requirements"></a> Requisitos
### <a name="build-settings-project--properties"></a>Configurações de compilação (projeto > Propriedades):
  1. **C/C++ > geral > formato de informações de depuração**: banco de dados do programa para editar e continuar ( `/ZI` )
  2. **C/C++ > geração de código > habilitar recompilação mínima**: Sim ( `/Gm` )
  3. **Vinculador > geral > habilitar vinculação incremental**: Sim ( `/INCREMENTAL` )

     Quaisquer configurações de vinculador incompatíveis (como `/SAFESEH` , ou `/OPT:` ...) devem causar aviso _LNK4075_ durante a compilação.  
     Exemplo: `LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification`

### <a name="debugger-settings-debug--options--general"></a>Configurações do depurador (opções de > de depuração > geral):
  - Habilitar editar e continuar nativo

     Qualquer compilador ou configuração de vinculador incompatíveis causará um erro durante editar e continuar.  
     Exemplo: `Edit and Continue : error  : ‘file.cpp’ in ‘MyApp.exe’ was not compiled with Edit and Continue enabled. Ensure that the file is compiled with the Program Database for Edit and Continue (/ZI) option.`

## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> Alterações sem suporte
 As seguintes alterações de C/C++ não podem ser aplicadas durante uma sessão de depuração. Se você fizer qualquer uma dessas alterações e, em seguida, tentar aplicar as alterações de código, uma mensagem de erro ou de aviso será exibida na janela de **saída** .

- A maioria das alterações aos dados globais ou estáticos.

- As alterações nos executáveis que são copiados de outro computador e não são criados localmente.

- As alterações para um tipo de dados que afeta o layout de um objeto, como, por exemplo, membros de dados de uma classe.

- Adicionando mais de 64k bytes do novo código ou dados.

- Adicionando variáveis que exigem um construtor em um ponto antes do ponteiro de instrução.

- As alterações que afetam o código que exigem a inicialização de tempo de execução.

- Adicionar manipuladores de exceção, em alguns casos.

- Alterações aos arquivos de recurso.

- Alterações ao código em arquivos somente leitura.

- Alterações ao código sem um arquivo PDB correspondente.

- Alterações ao código que não tem arquivo de objeto.

* Modificando lambdas que:
  - Ter um membro estático ou global.
  - São passados para um std:: function. Isso causa uma violação de ODR autêntica e resulta em C1092.

- Editar e Continuar não atualiza bibliotecas estáticas. Se você fizer uma alteração em uma biblioteca estática, a execução continuará com a versão antiga e nenhum aviso será emitido.

## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> Cenários sem suporte
 Editar e Continuar para C/C++ está indisponível nos seguintes cenários de depuração:

- Depurando aplicativos nativos compilados com [/zo (aprimorar a depuração otimizada)](/cpp/build/reference/zo-enhance-optimized-debugging)

- Em versões do Visual Studio anteriores ao Visual Studio 2015 atualização 1, depuração de aplicativos ou componentes UWP. A partir do Visual Studio 2015 atualização 1, você pode usar editar e continuar nos aplicativos e aplicativos do DirectX do UWP C++, pois ele agora dá suporte à `/ZI` opção de compilador com a  `/bigobj` opção. Você também pode usar editar e continuar com binários compilados com a `/FASTLINK` opção.

- Depuração de aplicativos da loja 8/8.1. Esses projetos usam o conjunto de ferramentas do VC 120 e a opção C/C++ `/bigobj` . Editar e continuar com `/bigobj` o só tem suporte no conjunto de ferramentas do VC 140.

- Depuração no Windows 98.

- Depuração de modo misto (nativo/gerenciado).

- Depuração de JavaScript.

- Depuração de SQL.

- Depurando um arquivo de despejo.

- Editando o código após uma exceção sem tratamento quando a opção **Desenrolar a pilha de chamadas em exceções não tratadas** não está selecionada.

- Depurando um aplicativo usando **Attach to** em vez de executar o aplicativo escolhendo **Iniciar** no menu **depurar** .

- Depurando código otimizado.

- Depurando uma versão antiga do código depois que uma nova versão não é compilada devido a erros de compilação.

- Usando um caminho de compilador personalizado (*cl.exe*). Por motivos de segurança, para a recompilação de um arquivo durante a edição e a continuação, o Visual Studio sempre usa o compilador instalado. Se você estiver usando um caminho de compilador personalizado (por exemplo, por meio de uma `$(ExecutablePath)` variável personalizada em seu `*.props` arquivo), um aviso será exibido e o Visual Studio retornará para usar o compilador instalado da mesma versão/arquitetura.

- Sistema de Build FASTBuild. Atualmente, o FASTBuild não é compatível com a opção de compilador "Enable Minimative Rebuild ( `/Gm` )" e, portanto, Edit and Continue não tem suporte.

- Arquiteturas herdadas/conjuntos de ferramentas do VC. Com o conjunto de ferramentas do VC 140, o depurador padrão dá suporte a editar e continuar com aplicativos x86 e x64. Os conjuntos de ferramentas herdados dão suporte apenas a aplicativos x86. Os conjuntos de ferramentas mais antigos que o VC 120 devem usar o depurador herdado marcando "_Opções de > de depuração > geral >_ usar o modo de compatibilidade nativo" para usar editar e continuar.

## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> Limitações de vinculação

### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Opções de vinculador que desabilitam Editar e Continuar
 As opções de vinculador a seguir desabilitam Editar e Continuar:

- Setting **/OPT: REF**, **/OPT: ICF**ou **/incremental: não** desabilita Edit and Continue com o seguinte aviso:  
     `LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT specification`

- Definir **/Order**, **/Release**ou **/Force** desabilita editar e continuar com o seguinte aviso:  
     `LINK : warning LNK4075: ignoring /INCREMENTAL due to /option specification`

- Definir qualquer opção que evite a criação de um arquivo de banco de dados do programa (.pdb) desabilita Editar e Continuar sem aviso específico.

### <a name="auto-relinking-limitations"></a><a name="BKMK_Auto_relinking_limitations"></a> Limitações de revinculação automática
 Por padrão, Editar e Continuar vincula novamente o programa ao final de uma sessão de depuração para criar um executável atualizado.

 Editar e Continuar não pode vincular o programa novamente se você o depurá-lo a partir de um local diferente do local de compilação original. Uma mensagem informa que você precisa recompilar manualmente.

 Editar e Continuar não recompila bibliotecas estáticas. Se você fizer alterações em uma biblioteca estática usando editar e continuar, será necessário recriar manualmente a biblioteca e vincular novamente os aplicativos que o utilizam.

 Editar e Continuar não invoca as etapas personalizadas de compilação. Se o seu programa usa etapas personalizadas de compilação, recompile manualmente de modo que as etapas personalizadas de compilação possam ser invocadas. Nesse caso, você pode desabilitar nova vinculação após Editar e Continuar para assegurar que seja solicitado a fazer a recompilação manualmente.

 **Para desabilitar a nova vinculação após Editar e Continuar**

1. No menu de **Depurar**, escolha **Opções e Configurações**.

2. Na caixa de diálogo **Opções** , no nó **depuração** e selecione o nó **Editar e continuar** .

3. Desmarque a caixa de seleção **Vincular novamente alterações de código após a depuração**.

## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_header_limitations"></a> Limitações de cabeçalho pré-compilado
 Por padrão, Editar e Continuar carrega e processa cabeçalhos pré-compilados no plano de fundo para acelerar o processamento de alterações de código. O carregamento de cabeçalhos pré-compilados requer a alocação de memória física, o que pode ser um problema se você estiver compilando em um computador com RAM limitada. Você pode determinar se isso pode ser um problema usando o Gerenciador de tarefas do Windows para determinar a quantidade de memória física disponível durante a depuração. Se esse valor for maior que o tamanho dos cabeçalhos pré-compilados, Editar e Continuar não terá problemas. Se o valor for menor que o tamanho dos cabeçalhos pré-compilados, você pode impedir que Editar e Continuar carregue cabeçalhos pré-compilados no plano de fundo.

 **Para desabilitar o carregamento em segundo plano de cabeçalhos pré-compilados para Editar e Continuar**

1. No menu de **Depurar**, escolha **Opções e Configurações**.

2. Na caixa de diálogo **Opções** , no nó **depuração** e selecione o nó **Editar e continuar** .

3. Desmarque a caixa de seleção **Permitir Pré-Compilação**.

## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_attribute_limitations"></a> Limitações de atributo IDL
 Editar e Continuar não regeneram arquivos IDL (definição da interface). Consequentemente, as alterações aos atributos de IDL não serão refletidas ao depurar. Para ver o resultado das alterações em atributos IDL, você deve parar a depuração e recompilar seu aplicativo. Editar e Continuar não gera um erro ou um aviso se os atributos de IDL tiverem sido alterados. Para obter mais informações, confira [Atributos de IDL](/cpp/windows/idl-attributes).

## <a name="diagnosing-issues"></a><a name="BKMK_Diagnosing_issues"></a> Diagnosticando problemas
 Se o seu cenário não se ajustar a nenhuma das condições mencionadas acima, você poderá reunir mais detalhes Configurando o seguinte valor do Registro DWORD:
 1. Abra um Prompt de Comando do Desenvolvedor.
 2. Execute o comando a seguir:  
     `VsRegEdit.exe set “C:\Program Files (x86)\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`

 Definir esse valor no início de uma sessão de depuração faz com que os vários componentes do Edit e continuem a Spew log **Output Window**detalhado no painel de  >  **depuração** janela de saída.

## <a name="see-also"></a>Confira também
- [Editar e continuar (C++)](../debugger/edit-and-continue-visual-cpp.md)
