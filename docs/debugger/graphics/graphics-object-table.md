---
title: Tabela de objeto gráfico | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20a78d7bb3e27ddfd0a5a248436b5c5392558410
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848431"
---
# <a name="graphics-object-table"></a>Tabela de objetos de gráfico
A tabela de objeto de elementos gráficos em análise de gráficos do Visual Studio ajuda você a entender os objetos Direct3D que dão suporte a um quadro do seu jogo ou aplicativo.

 Essa é a tabela de objeto:

 ![Os objetos Direct3D que foram criados por um aplicativo.](media/gfx_diag_demo_object_table_orientation.png "gfx_diag_demo_object_table_orientation")

## <a name="understanding-the-graphics-object-table"></a>Noções básicas sobre a Tabela de Objetos Gráficos
 Usando a tabela de objetos, você pode analisar os objetos Direct3D que dão suporte a renderização de um quadro específico. Você pode identificar um problema de renderização para um objeto específico, examinando suas propriedades e os dados (usando outras ferramentas de diagnóstico de gráficos inicialmente no diagnóstico, você pode restringir a lista de objetos que podem não ser o esperado.) Quando encontrar o objeto incorreto, você pode usar uma visualização que é específica para seu tipo para examiná-lo — por exemplo, você pode usar o Editor de imagens para exibir texturas, ou o *Visualizador de Buffer* para exibir o conteúdo do buffer.

 A tabela de objetos dá suporte a copiar e colar para que você possa usar outra ferramenta — por exemplo, o Microsoft Excel — para examinar seu conteúdo.

 Além disso, você pode usar o **tipo** lista suspensa na parte superior esquerda para alternar a exibição de objetos do tipo **Buffers**, **sombreadores** ou **texturas**, ou todos esses itens ao mesmo tempo.  Além disso, você pode usar a caixa de pesquisa no canto superior direito para localizar linhas específicas em todos os dados que são apresentados.  Por exemplo, você pode procurar *D32_FLOAT* para localizar todas as instâncias de objetos de formato na lista.

### <a name="graphics-object-table-format"></a>Formato da Tabela de Objetos Gráficos
 A tabela de objetos exibe os objetos Direct3D e recursos que dão suporte ao quadro associado ao evento selecionado — por exemplo, estado objetos, buffers, sombreadores, texturas e outros recursos. Objetos que foram criados em um quadro anterior, mas não são usados durante o quadro capturado, são omitidos da tabela de objetos. Objetos que tenham sido destruídos pelo eventos anteriores durante o quadro capturado são omitidos nos eventos subsequentes. Objetos que não são definidos no D3D10Device ou D3D11DeviceContext são exibidos como texto cinza. Os objetos são exibidos em um formato de tabela.

|Column|Descrição|
|------------|-----------------|
|**Identificador**|O ID do objeto.|
|**Nome**|Informações específicas do aplicativo que foi definido no objeto usando a função Direct3D `SetPrivateData`, normalmente para fornecer informações adicionais de identificação sobre um objeto.|
|**Tipo**|O tipo de objeto.|
|**Ativo**|Exibe "*" para um objeto que foi definido no D3D10Device ou D3D11DeviceContext durante o quadro capturado.<br /><br /> Isso corresponde aos objetos que são exibidos como texto cinza, mas fornece uma entrada de coluna que você pode usar para classificar a tabela de objetos.|
|**Size**|O tamanho do objeto em bytes.|
|**Formatar**|O formato do objeto. Por exemplo, o formato de um objeto de textura ou o modelo de sombreador de um objeto sombreador.|
|**Largura**|A largura de um objeto de textura. Não se aplica a outros tipos de objeto.|
|**Altura**|A altura de um objeto de textura. Não se aplica a outros tipos de objeto.|
|**Profundidade**|A profundidade de um objeto de textura 3D. Se uma textura não for 3D, o valor é 0. Não se aplica a outros tipos de objeto.|
|**Mips**|O número de níveis de MIP que um objeto de textura possui. Não se aplica a outros tipos de objeto.|
|**ArraySize**|O número de texturas em uma matriz de textura. O intervalo é de 1 a um limite superior definido pelo nível de recurso atual. Para um mapa de cubo, esse valor é 6 vezes o número de mapas de cubo na matriz.|
|**Amostras**|O número de multisamples por pixel.|

## <a name="graphics-object-viewers"></a>Visualizadores de objeto gráfico
 Para exibir detalhes sobre um objeto, abra-o escolhendo seu nome na tabela de objetos. Detalhes do objeto são exibidos em formatos diferentes, dependendo do tipo do objeto. Por exemplo, as texturas são exibidas usando o Visualizador de textura e estado do dispositivo, como o contexto de dispositivo D3D11 é exibido como uma lista formatada. Versões diferentes do Direct3D fazer uso de objetos diferentes e geralmente são visualizadores específicos para os objetos mais importantes de cada versão.

 Aqui está o Visualizador de textura que mostra o conteúdo do estágio de pipeline a fusão de saída.

 ![A visualização de textura exibindo a fusão de saída](media/gfx_diag_texture_preview.png "gfx_diag_texture_preview")

### <a name="d3d12-command-list"></a>Lista de comandos D3D12
 No Direct3D 12 uma lista de comandos é um objeto que grava os comandos em um alocador de comando para que eles possam ser enviados à GPU como uma única solicitação. Listas de comando geralmente executam uma série de configuração de estado, desenham, limpam e copiar os comandos. Eles são particularmente importantes porque elas são o método preferencial de renderização Direct3D 12 e podem ser usadas novamente entre os quadros para ajudar a aumentar o desempenho. Detalhes da lista de comandos são exibidos em uma nova janela de documento, com informações relacionadas a cada estágio do pipeline apresentado em sua própria guia.

### <a name="d3d12-pipeline-state-object-pso"></a>Objeto de estado do Pipeline D3D12 (PSO l)
 No Direct3D 12, um objeto de estado do pipeline representa uma parte significativa do estado GPU, incluindo atualmente todos os sombreadores de conjunto e determinados objetos de estado da função fixa. Depois de criado, um objeto de estado do pipeline é imutável — um aplicativo só pode alterar a configuração do pipeline, associando a um objeto de estado de outro pipeline. Detalhes do PSO são exibidos em uma nova janela de documento, com detalhes da configuração do pipeline dispostos hierarquicamente.

### <a name="d3d12-root-signature"></a>Assinatura de raiz D3D12
 No Direct3D 12, a assinatura de raiz define todos os recursos que estão associados a um pipeline de gráficos ou de computação, e ele comando listas de links para os recursos que exige que os sombreadores. Normalmente há uma assinatura de raiz para gráficos e outra para a computação em um aplicativo. Detalhes de assinatura de raiz são exibidos em uma nova janela de documento, com detalhes da assinatura de raiz dispostos hierarquicamente.

### <a name="d3d12-resources"></a>Recursos D3D12
 No Direct3D 12, os recursos são captura todos os objetos que fornecem dados para o pipeline de renderização; Isso é diferente de Direct3D11 que muitos objetos específicos para diferentes tipos e as dimensões de recursos definidos. Um recurso do Direct3D 12 pode conter dados de textura, dados de vértice, os dados do sombreador e muito mais — eles podem até mesmo representar destinos de renderização, como o buffer de profundidade. Detalhes de um recurso do Direct3D 12 são exibidos em uma nova janela do documento. Análise de gráficos usará o visualizador apropriado para o conteúdo do objeto de recurso se ele é capaz de determinar seu tipo. Por exemplo, um objeto de recurso que contém dados de textura é exibido usando o Visualizador de textura, assim como um objeto Texture2D D3D11 é.

### <a name="device-context-object"></a>Objeto de contexto de dispositivo
 No Direct3D 11 e Direct3D 10, o contexto de dispositivo (**contexto de dispositivo D3D11** ou **dispositivo D3D10**) objeto é particularmente importante porque ele contém as informações de estado mais importantes, estando vinculado a outros objetos de estado que são definidos no momento. Detalhes do contexto de dispositivo são exibidos em uma nova janela de documentos e cada categoria de informações é apresentada em sua própria guia. As alterações de contexto de dispositivo quando um novo evento é selecionado para refletir o estado atual do dispositivo.

### <a name="buffer-object"></a>Objeto de buffer
 Detalhes do objeto de buffer (Buffer D3D11 ou D3D10) são exibidos em uma nova janela de documento que apresenta o conteúdo de buffer em uma tabela e fornece uma interface para alterar como o conteúdo de buffer é exibido. A tabela de **dados do buffer** dá suporte a copiar e colar para que você possa usar outra ferramenta, como por exemplo, o Microsoft Excel, para examinar seu conteúdo. O conteúdo do buffer é interpretado de acordo com o valor da **formato** caixa de combinação, localizada acima da tabela de **dados do buffer**. Na caixa, você pode inserir um formato de dados compostos que consiste em tipos de dados listados na tabela a seguir. Por exemplo, "float int" exibe uma lista de estruturas que contêm um valor de ponto flutuante de 32 bits seguido por um valor inteiro com sinal de 32 bits. Formatos de dados compostos que você especificou são adicionados à caixa de combinação para uso posterior.

 Você também pode alternar os **Mostrar deslocamentos** caixa de seleção para ocultar ou exibir o deslocamento de cada elemento do buffer.

|Tipo|Descrição|
|----------|-----------------|
|**float**|Um valor de ponto flutuante de 32 bits.|
|**float2**|Um vetor que contém dois valores de ponto flutuante de 32 bits.|
|**float3**|Um vetor que contém três valores de ponto flutuante de 32 bits.|
|**float4**|Um vetor que contém quatro valores de ponto flutuante de 32 bits.|
|**byte**|Um valor inteiro com sinal de 8 bits.|
|**2byte**|Um valor inteiro com sinal de 16 bits.|
|**4byte**|Um valor inteiro com sinal de 32 bits. O mesmo que **int**.|
|**8byte**|Um valor inteiro com sinal de 64 bits. O mesmo que **int64**.|
|**xbyte**|Um valor hexadecimal de 8 bits.|
|**x2byte**|Um valor hexadecimal de 16 bits.|
|**x4byte**|Um valor hexadecimal de 32 bits. O mesmo que **xint**.|
|**x8byte**|Um valor hexadecimal de 64 bits. O mesmo que **xint64**.|
|**ubyte**|Um valor inteiro sem sinal de 8 bits.|
|**u2byte**|Um valor inteiro sem sinal de 16 bits.|
|**u4byte**|Um valor inteiro sem sinal de 32 bits. O mesmo que **uint**.|
|**u8byte**|Um valor inteiro sem sinal de 64 bits. O mesmo que **uint64**.|
|**half**|Um valor de ponto flutuante de 16 bits.|
|**half2**|Um vetor que contém dois valores de ponto flutuante de 16 bits.|
|**half3**|Um vetor que contém três valores de ponto flutuante de 16 bits.|
|**half4**|Um vetor que contém quatro valores de ponto flutuante de 16 bits.|
|**double**|Um valor de ponto flutuante de 64 bits.|
|**int**|Um valor inteiro com sinal de 32 bits. O mesmo que **4byte**.|
|**int64**|Um valor inteiro com sinal de 64 bits. O mesmo que **8byte**.|
|**xint**|Um valor hexadecimal de 32 bits. O mesmo que **x4byte**.|
|**xint64**|Um valor hexadecimal de 64 bits. O mesmo que **x8byte**.|
|**uint**|Um valor inteiro sem sinal de 32 bits. O mesmo que **u4byte**.|
|**uint64**|Um valor inteiro sem sinal de 64 bits. O mesmo que **u8byte**.|
|**bool**|Um valor booleano (`true` ou `false`). Cada valor booleano é representado por um valor de 32 bits.|

## <a name="see-also"></a>Consulte também
- [Diagnóstico de gráficos (depuração de gráficos DirectX)](visual-studio-graphics-diagnostics.md)
- [Passo a passo: Objetos ausentes devido ao estado do dispositivo](walkthrough-missing-objects-due-to-device-state.md)