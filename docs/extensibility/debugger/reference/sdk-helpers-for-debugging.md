---
title: Ajudantes sdk para depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9edb7c508fdea6736a71c0f70c0d2ff305d4a399
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713644"
---
# <a name="sdk-helpers-for-debugging"></a>Auxiliares do SDK para depuração
Essas funções e declarações são funções de ajuda global para implementar mecanismos de depuração, avaliadores de expressão e provedores de símbolos em C++.

> [!NOTE]
> Não há versões gerenciadas dessas funções e declarações no momento.

## <a name="overview"></a>Visão geral
 Para que os mecanismos de depuração, avaliadores de expressão e provedores de símbolos sejam usados pelo Visual Studio, eles devem ser registrados. Isso é feito definindo subchaves e entradas de registro, também conhecidas como "definição de métricas". As seguintes funções globais são projetadas para facilitar o processo de atualização dessas métricas. Consulte a seção em Locais de Registro para descobrir o layout de cada subchave de registro atualizada por essas funções.

## <a name="general-metric-functions"></a>Funções métricas gerais
 Estas são funções gerais usadas por motores de depuração. Funções especializadas para avaliadores de expressão e provedores de símbolos são detalhadas posteriormente.

### <a name="getmetric-method"></a>Método GetMetric
 Recupera um valor métrico do registro.

```cpp
HRESULT GetMetric(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   DWORD * pdwValue,
   LPCWSTR pszAltRoot
);
```

|Parâmetro|Descrição|
|---------------|-----------------|
|pszMachine|[em] Nome de uma máquina possivelmente remota`NULL` cujo registro será escrito (significa máquina local).|
|pszType|[em] Um dos tipos métricos.|
|guidSection|[em] GUID de um motor específico, avaliador, exceção, etc. Isso especifica uma subseção em um tipo métrico para um elemento específico.|
|pszMetric|[em] A métrica a ser obtida. Isso corresponde a um nome de valor específico.|
|pdwValue|[em] O local de armazenamento do valor a partir da métrica. Existem vários sabores de GetMetric que podem retornar um DWORD (como neste exemplo), um BSTR, um GUID ou uma matriz de GUIDs.|
|pszAltRoot|[em] Uma raiz de registro alternativa para usar. Configurado `NULL` para usar o padrão.|

### <a name="setmetric-method"></a>Método SetMetric
 Define o valor métrico especificado no registro.

```cpp
HRESULT SetMetric(
         LPCWSTR pszType,
         REFGUID guidSection,
         LPCWSTR pszMetric,
   const DWORD   dwValue,
         bool    fUserSpecific,
         LPCWSTR pszAltRoot
);
```

|Parâmetro|Descrição|
|---------------|-----------------|
|pszType|[em] Um dos tipos métricos.|
|guidSection|[em] GUID de um motor específico, avaliador, exceção, etc. Isso especifica uma subseção em um tipo métrico para um elemento específico.|
|pszMetric|[em] A métrica a ser obtida. Isso corresponde a um nome de valor específico.|
|Dwvalue|[em] A localização de armazenamento do valor na métrica. Existem vários sabores de SetMetric que podem armazenar um DWORD (neste exemplo), um BSTR, um GUID ou uma matriz de GUIDs.|
|fUserSpecific|[em] TRUE se a métrica for específica do usuário e se ela deve ser escrita na colmeia do usuário em vez da colmeia da máquina local.|
|pszAltRoot|[em] Uma raiz de registro alternativa para usar. Configurado `NULL` para usar o padrão.|

### <a name="removemetric-method"></a>Método removemétrico
 Remove a métrica especificada do registro.

```cpp
HRESULT RemoveMetric(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   LPCWSTR pszAltRoot
);
```

|Parâmetro|Descrição|
|---------------|-----------------|
|pszType|[em] Um dos tipos métricos.|
|guidSection|[em] GUID de um motor específico, avaliador, exceção, etc. Isso especifica uma subseção em um tipo métrico para um elemento específico.|
|pszMetric|[em] A métrica a ser removida. Isso corresponde a um nome de valor específico.|
|pszAltRoot|[em] Uma raiz de registro alternativa para usar. Configurado `NULL` para usar o padrão.|

### <a name="enummetricsections-method"></a>Método EnumMetricSections
 Enumera as várias seções métricas no registro.

```cpp
HRESULT EnumMetricSections(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   GUID *  rgguidSections,
   DWORD * pdwSize,
   LPCWSTR pszAltRoot
);
```

|Parâmetro|Descrição|
|---------------|-----------------|
|pszMachine|[em] Nome de uma máquina possivelmente remota`NULL` cujo registro será escrito (significa máquina local).|
|pszType|[em] Um dos tipos métricos.|
|rgguidSeções|[dentro, fora] Matriz pré-alocada de GUIDs a serem preenchidos.|
|Pdwsize|[em] O número máximo de GUIDs que `rgguidSections` podem ser armazenados na matriz.|
|pszAltRoot|[em] Uma raiz de registro alternativa para usar. Configurado `NULL` para usar o padrão.|

## <a name="expression-evaluator-functions"></a>Funções avaliadoras de expressão

|Função|Descrição|
|--------------|-----------------|
|GeteeMetric|Recupera um valor métrico do registro.|
|SeteeMetric|Define o valor métrico especificado no registro.|
|RemoveEEMetric|Remove a métrica especificada do registro.|
|GetEEMetricFile|Obtém um nome de arquivo a partir da métrica especificada e o carrega, retornando o conteúdo do arquivo como uma seqüência.|

## <a name="exception-functions"></a>Funções de exceção

|Função|Descrição|
|--------------|-----------------|
|GetExceptionMetric|Recupera um valor métrico do registro.|
|SetExceptionMetric|Define o valor métrico especificado no registro.|
|RemoveExceptionMetric|Remove a métrica especificada do registro.|
|RemoveAllExceptionMetrics|Remove todas as métricas de exceção do registro.|

## <a name="symbol-provider-functions"></a>Funções do provedor de símbolos

|Função|Descrição|
|--------------|-----------------|
|GetSPMetric|Recupera um valor métrico do registro.|
|SetSPMetric|Define o valor métrico especificado no registro.|
|RemoveSPMetric|Remove a métrica especificada do registro.|

## <a name="enumeration-functions"></a>Funções de enumeração

|Função|Descrição|
|--------------|-----------------|
|EnumMetricSections|Enumera todas as métricas para um tipo métrico especificado.|
|EnumDebugEngine|Enumera os motores de depuração registrados.|
|EnumEEs|Enumera os avaliadores de expressão registrados.|
|EnumExceptionMetrics|Enumera todas as métricas de exceção.|

## <a name="metric-definitions"></a>Definições métricas
 Essas definições podem ser usadas para nomes métricos predefinidos. Os nomes correspondem a várias chaves de registro e nomes de `extern LPCWSTR metrictypeEngine`valor e são todos definidos como strings de caracteres largos: por exemplo, .

|Tipos métricos predefinidos|Descrição: A chave base para...|
|-----------------------------|---------------------------------------|
|metrictypeEngine|Todas as métricas do motor de depuração.|
|metrictypePortFornecedor|Todas as métricas do fornecedor de porta.|
|tipo métricoExceção|Todas as métricas de exceção.|
|metricttypeEEExtensão|Todas as extensões do avaliador de expressão.|

|Propriedades do motor de depuração|Descrição|
|-----------------------------|-----------------|
|métricoAddressBP|Definido como não zero para indicar suporte para pontos de interrupção de endereço.|
|métricaAlwaysLoadLocal|Definir como não zero, a fim de sempre carregar o motor de depuração localmente.|
|metricLoadInDebuggeeSession|NÃO USADO|
|métricaLoadedByDepuraver|Definido como não zero para indicar que o motor de depuração estará sempre carregado com ou pelo programa que está sendo depurado.|
|métricaAnexar|Definir como não zero para indicar suporte para apego aos programas existentes.|
|métricoCallStackBP|Definido como não zero para indicar suporte para pontos de interrupção da pilha de chamadas.|
|métricaConditionalBP|Definir como não zero para indicar suporte para a configuração de pontos de interrupção condicional.|
|metricDataBP|Definido como não zero para indicar suporte para a configuração de pontos de interrupção em alterações nos dados.|
|metricDisassembly|Definir como não zero para indicar suporte para a produção de uma listagem de desmontagem.|
|métricaDumpWriting|Definir como não zero para indicar suporte para escrita de despejo (o dumping de memória para um dispositivo de saída).|
|métricoENC|Definir como não zero para indicar suporte para Editar e Continuar. **Nota:**  Um motor de depuração personalizado nunca deve definir isso ou deve sempre defini-lo como 0.|
|métricaExceções|Definir como não zero para indicar suporte para exceções.|
|metricFunctionBP|Definido como não zero para indicar suporte para pontos de interrupção nomeados (pontos de interrupção que quebram quando um determinado nome de função é chamado).|
|metricHitCountBP|Definido como não zero para indicar suporte para a configuração de pontos de interrupção de "ponto de impacto" (pontos de interrupção que são acionados somente após serem atingidos um certo número de vezes).|
|métricaJITDebug|Definido como não zero para indicar suporte para depuração just-in-time (o depurador é iniciado quando uma exceção ocorre em um processo em execução).|
|metricMemory|NÃO USADO|
|métricoPortSupplier|Defina isso no CLSID do fornecedor portuário se um for implementado.|
|métricaregistros|NÃO USADO|
|metricSetNextStatement|Definir como não zero para indicar suporte para definir a próxima instrução (que ignora a execução de instruções intermediárias).|
|metricSuspendThread|Definir como não zero para indicar suporte para suspender a execução do segmento.|
|metricWarnIfNosymbols|Definido como não zero para indicar que o usuário deve ser notificado se não houver símbolos.|
|metricProgramProvider|Defina isso no CLSID do provedor do programa.|
|métricaAlwaysLoadProgramProviderLocal|Defina isso como não zero para indicar que o provedor do programa deve ser sempre carregado localmente.|
|métricoEngineCanWatchProcess|Defina isso como não zero para indicar que o mecanismo de depuração observará eventos de processo em vez do provedor do programa.|
|metricDebugging remoto|Defina isso como não zero para indicar suporte para depuração remota.|
|métricoEncUseNativeBuilder|Defina isso como não zero para indicar que o Gerenciador editar e continuar deve usar o encbuild.dll do mecanismo de depuração para criar para Editar e Continuar. **Nota:**  Um motor de depuração personalizado nunca deve definir isso ou deve sempre defini-lo como 0.|
|métricaLoadUnderWOW64|Defina isso como não zero para indicar que o mecanismo de depuração deve ser carregado no processo de depuração em WOW ao depurar um processo de 64 bits; caso contrário, o motor de depuração será carregado no processo Visual Studio (que está funcionando sob WOW64).|
|métricoCarregarprogramaProvedorUnderWOW64|Defina isso como não zero para indicar que o provedor de programa deve ser carregado no processo de depuração ao depurar um processo de 64 bits em WOW; caso contrário, ele será carregado no processo visual studio.|
|métricaStopOnExceptionCrossingManagedBoundary|Defina isso como não zero para indicar que o processo deve parar se uma exceção não tratada for lançada através dos limites de código gerenciados/não gerenciados.|
|métricoAutoSelectPrioridade|Defina isso como prioridade para a seleção automática do motor de depuração (valores mais altos são iguais a prioridade superior).|
|métricoAutoSelectListaincompatível|Chave de registro contendo entradas que especificam GUIDs para mecanismos de depuração a serem ignoradas na seleção automática. Estas entradas são um número (0, 1, 2, e assim por diante) com um GUID expresso como uma string.|
|metricIncompatibleList|Chave de registro contendo entradas que especificam GUIDs para mecanismos de depuração incompatíveis com este mecanismo de depuração.|
|métricaDisableJITOtimização|Defina isso como não zero para indicar que otimizações just-in-time (para código gerenciado) devem ser desativadas durante a depuração.|

|Propriedades do avaliador de expressão|Descrição|
|-------------------------------------|-----------------|
|metricEngine|Isso contém o número de mecanismos de depuração que suportam o avaliador de expressão especificado.|
|métricoPréloadModules|Defina isso como não zero para indicar que os módulos devem ser pré-carregados quando um avaliador de expressão é lançado contra um programa.|
|métricaThisObjectName|Defina isso no nome do objeto "este".|

|Propriedades de extensão avaliadora de expressão|Descrição|
| - |-----------------|
|métricaExtensionDll|Nome da dll que suporta esta extensão.|
|metricExtensionRegistersSuportado|Lista de registros suportados.|
|metricExtensionRegistersEntryPoint|Ponto de entrada para acesso aos registros.|
|metricExtensionTypesSupported|Lista de tipos suportados.|
|metricExtensTypesEntryPoint|Ponto de entrada para tipos de acesso.|

|Propriedades do fornecedor portuário|Descrição|
|------------------------------|-----------------|
|métricaPortPickerCLSID|O CLSID do seletor de portas (uma caixa de diálogo que o usuário pode usar para selecionar portas e adicionar portas para usar para depuração).|
|metricDisallowUserEnteredPorts|Não zero se as portas inseridas pelo usuário não puderem ser adicionadas ao fornecedor de porta (isso torna a caixa de diálogo seletor de portas essencialmente somente leitura).|
|métricaPidBase|O ID do processo base usado pelo fornecedor da porta ao alocar IDs de processo.|

|Tipos de armazenamento de SP predefinidos|Descrição|
|-------------------------------|-----------------|
|storetypeFile|Os símbolos são armazenados em um arquivo separado.|
|armazenamentoTypeMetadados|Os símbolos são armazenados como metadados em uma montagem.|

|Propriedades Diversas|Descrição|
|------------------------------|-----------------|
|métricaShowNonUserCode|Defina isso como não zero para mostrar código de não-usuário.|
|métricaJustMyCodeStepping|Defina isso como não zero para indicar que a revisão só pode ocorrer no código do usuário.|
|metricCLSID|CLSID para um objeto de um tipo métrico específico.|
|metricName|Nome fácil de usar para um objeto de um tipo métrico específico.|
|métricaLinguagem|Nome do idioma.|

## <a name="registry-locations"></a>Locais de registro
 As métricas são lidas e escritas no `VisualStudio` registro, especificamente na subchave.

> [!NOTE]
> Na maioria das vezes, as métricas serão escritas para a chave HKEY_LOCAL_MACHINE. No entanto, às vezes HKEY_CURRENT_USER será a chave de destino. Dbgmetric.lib manipula ambas as teclas. Ao obter uma métrica, ele pesquisa HKEY_CURRENT_USER primeiro, depois HKEY_LOCAL_MACHINE. Quando está definindo uma métrica, um parâmetro especifica qual chave de nível superior deve ser usada.

 *[chave de registro]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[raiz da versão]*\

 *[raiz métrica]*\

 *[tipo métrico]*\

 *[métrica] = [valor métrico]*

 *[métrica] = [valor métrico]*

 *[métrica] = [valor métrico]*

|Espaço reservado|Descrição|
|-----------------|-----------------|
|*[chave de registro]*|`HKEY_CURRENT_USER` ou `HKEY_LOCAL_MACHINE`.|
|*[raiz da versão]*|A versão do Visual Studio `7.0` `7.1`(por `8.0`exemplo, ou ). No entanto, esta raiz também pode ser modificada usando o interruptor **/rootsufix** para **devenv.exe**. Para VSIP, este modificador é tipicamente **Exp**, então a raiz da versão seria, por exemplo, 8.0Exp.|
|*[raiz métrica]*|Isto `AD7Metrics` é `AD7Metrics(Debug)`ou, dependendo se a versão de depuração do dbgmetric.lib é usada. **Nota:**  Se dbgmetric.lib é usado ou não, esta convenção de nomeação deve ser respeitada se você tiver diferenças entre versões de depuração e versão que devem ser refletidas no registro.|
|*[tipo métrico]*|O tipo de métrica `Engine`a `ExpressionEvaluator` `SymbolProvider`ser escrita: , , etc. Todos eles são definidos como em `metricTypeXXXX`dbgmetric.h as , onde `XXXX` está o nome de tipo específico.|
|*[métrica]*|O nome de uma entrada a ser atribuída a um valor a fim de definir a métrica. A organização real das métricas depende do tipo métrico.|
|*[valor métrico]*|O valor atribuído à métrica. O tipo que o valor deve ter (string, number, etc.) depende da métrica.|

> [!NOTE]
> Todos os GUIDs são `{GUID}`armazenados no formato de . Por exemplo, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Motores de depuração
 A seguir está a organização das métricas dos motores de depuração no registro. `Engine`é o nome de tipo métrico para um mecanismo de depuração e corresponde a *[tipo métrico]* na subárvore de registro acima.

 `Engine`\

 *[guia do motor]*\

 `CLSID` = *[orientação de classe]*

 *[métrica] = [valor métrico]*

 *[métrica] = [valor métrico]*

 *[métrica] = [valor métrico]*

 `PortSupplier`\

 `0` = *[orientação do fornecedor portuário]*

 `1` = *[orientação do fornecedor portuário]*

|Espaço reservado|Descrição|
|-----------------|-----------------|
|*[guia do motor]*|O GUID do motor de depuração.|
|*[orientação de classe]*|O GUID da classe que implementa este motor de depuração.|
|*[orientação do fornecedor portuário]*|O GUID do fornecedor portuário, se houver. Muitos motores de depuração usam o fornecedor de porta padrão e, portanto, não especificam seu próprio fornecedor. Neste caso, a `PortSupplier` subchave estará ausente.|

### <a name="port-suppliers"></a>Fornecedores de porta
 A seguir está a organização das métricas do fornecedor portuário no registro. `PortSupplier`é o nome de tipo métrico para um fornecedor de porta e corresponde ao *[tipo métrico]*.

 `PortSupplier`\

 *[orientação do fornecedor portuário]*\

 `CLSID` = *[orientação de classe]*

 *[métrica] = [valor métrico]*

 *[métrica] = [valor métrico]*

|Espaço reservado|Descrição|
|-----------------|-----------------|
|*[orientação do fornecedor portuário]*|O GUID do fornecedor portuário|
|*[orientação de classe]*|O GUID da classe que implementa este fornecedor portuário|

### <a name="symbol-providers"></a>Provedores de símbolos
 A seguir está a organização das métricas do fornecedor de símbolos no registro. `SymbolProvider`é o nome do tipo métrico para o provedor de símbolos e corresponde ao *[tipo métrico]*.

 `SymbolProvider`\

 *[guia do provedor de símbolos]*\

 `file`\

 `CLSID` = *[orientação de classe]*

 *[métrica] = [valor métrico]*

 *[métrica] = [valor métrico]*

 `metadata`\

 `CLSID` = *[orientação de classe]*

 *[métrica] = [valor métrico]*

 *[métrica] = [valor métrico]*

|Espaço reservado|Descrição|
|-----------------|-----------------|
|*[guia do provedor de símbolos]*|O GUID do provedor de símbolos|
|*[orientação de classe]*|O GUID da classe que implementa este provedor de símbolos|

### <a name="expression-evaluators"></a>Avaliadores de expressão
 A seguir está a organização das métricas avaliadoras de expressão no registro. `ExpressionEvaluator`é o nome do tipo métrico para o avaliador de expressão e corresponde ao *[tipo métrico]*.

> [!NOTE]
> O tipo `ExpressionEvaluator` métrico para não é definido em dbgmetric.h, pois supõe-se que todas as alterações métricas `ExpressionEvaluator` para avaliadores de expressão passarão pelas funções métricas do avaliador de expressão apropriadas (o layout da subchave é um pouco complicado, de modo que os detalhes estão escondidos dentro dbgmetric.lib).

 `ExpressionEvaluator`\

 *[orientação linguística]*\

 *[guia do fornecedor]*\

 `CLSID` = *[orientação de classe]*

 *[métrica] = [valor métrico]*

 *[métrica] = [valor métrico]*

 `Engine`\

 `0` = *[guia do motor de depuração]*

 `1` = *[guia do motor de depuração]*

|Espaço reservado|Descrição|
|-----------------|-----------------|
|*[orientação linguística]*|O GUID de uma língua|
|*[guia do fornecedor]*|O GUID de um fornecedor|
|*[orientação de classe]*|O GUID da classe que implementa este avaliador de expressão|
|*[guia do motor de depuração]*|O GUID de um mecanismo de depuração que este avaliador de expressão trabalha com|

### <a name="expression-evaluator-extensions"></a>Extensões avaliadoras de expressão
 A seguir está a organização das métricas de extensão do avaliador de expressão no registro. `EEExtensions`é o nome do tipo métrico para as extensões do avaliador de expressão e corresponde ao *[tipo métrico]*.

 `EEExtensions`\

 *[guia de extensão]*\

 *[métrica] = [valor métrico]*

 *[métrica] = [valor métrico]*

|Espaço reservado|Descrição|
|-----------------|-----------------|
|*[guia de extensão]*|O GUID de uma extensão avaliadora de expressão|

### <a name="exceptions"></a>Exceções
 A seguir está a organização das métricas de exceções no registro. `Exception`é o nome do tipo métrico para as exceções e corresponde ao *[tipo métrico]*.

 `Exception`\

 *[guia do motor de depuração]*\

 *[tipos de exceção]*\

 *[exceção]*\

 *[métrica] = [valor métrico]*

 *[métrica] = [valor métrico]*

 *[exceção]*\

 *[métrica] = [valor métrico]*

 *[métrica] = [valor métrico]*

|Espaço reservado|Descrição|
|-----------------|-----------------|
|*[guia do motor de depuração]*|O GUID de um mecanismo de depuração que suporta exceções.|
|*[tipos de exceção]*|Um título geral para a subchave identificando a classe de exceções que podem ser manuseadas. Nomes típicos são **Exceções C++,** **Exceções win32,** **exceções de tempo de execução de idiomas comuns**e **verificações nativas de tempo de execução**. Esses nomes também são usados para identificar uma classe específica de exceção ao usuário.|
|*[exceção]*|Um nome para uma exceção: por exemplo, **_com_error** ou **Control-Break**. Esses nomes também são usados para identificar uma exceção específica ao usuário.|

## <a name="requirements"></a>Requisitos
 Esses arquivos estão localizados no diretório de instalação do [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK (por padrão, *[unidade]* \Arquivos do programa\Microsoft Visual Studio 2010 SDK\\).

 Cabeçalho: inclui\dbgmetric.h

 Biblioteca: libs\ad2de.lib, libs\dbgmetric.lib

## <a name="see-also"></a>Confira também
- [Referência da API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
