---
title: Tabela de objetos gráficos | Microsoft Docs
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
ms.openlocfilehash: ea80420b2146bd8c604a95d71012009dcb940ef5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735444"
---
# <a name="graphics-object-table"></a>Tabela de objetos de gráfico
A tabela de objetos gráficos na análise de gráficos do Visual Studio ajuda a entender os objetos do Direct3D que dão suporte a um quadro de seu jogo ou aplicativo.

 Esta é a tabela de objetos:

 ![Objetos do Direct3D que foram criados por um aplicativo.](media/gfx_diag_demo_object_table_orientation.png "gfx_diag_demo_object_table_orientation")

## <a name="understanding-the-graphics-object-table"></a>Noções básicas sobre a Tabela de Objetos Gráficos
 Usando a tabela de objetos, você pode analisar os objetos do Direct3D que dão suporte à renderização de um quadro específico. Você pode identificar um problema de renderização para um objeto específico examinando suas propriedades e seus dados (usando outras ferramentas de Diagnóstico de Gráficos anteriormente em seu diagnóstico, você pode restringir a lista de objetos que talvez não sejam o que você espera.) Quando você encontrar o objeto incorreto, poderá usar uma visualização específica para seu tipo para examiná-lo — por exemplo, você pode usar o editor de imagem para exibir texturas ou o *Visualizador de buffer* para exibir o conteúdo do buffer.

 A tabela de objetos dá suporte a copiar e colar para que você possa usar outra ferramenta — por exemplo, o Microsoft Excel — para examinar seu conteúdo.

 Além disso, você pode usar o menu suspenso de **tipo** no canto superior esquerdo para alternar a exibição de objetos de **buffers**de tipo, **sombreadores** ou **texturas**ou todos esses itens de uma só vez.  Além disso, você pode usar a caixa de pesquisa no canto superior direito para localizar linhas específicas em todos os dados apresentados.  Por exemplo, você pode pesquisar por *D32_FLOAT* para localizar todas as instâncias de objetos desse formato na lista.

### <a name="graphics-object-table-format"></a>Formato da Tabela de Objetos Gráficos
 A tabela de objetos exibe os objetos e recursos do Direct3D que dão suporte ao quadro associado ao evento selecionado — por exemplo, objetos de estado, buffers, sombreadores, texturas e outros recursos. Objetos que foram criados em um quadro anterior, mas não são usados durante o quadro capturado, são omitidos da tabela de objetos. Objetos que tenham sido destruídos pelo eventos anteriores durante o quadro capturado são omitidos nos eventos subsequentes. Objetos que não são definidos no D3D10Device ou D3D11DeviceContext são exibidos como texto cinza. Os objetos são exibidos em um formato de tabela.

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
|**ArraySize**|O número de texturas em uma matriz de textura. O intervalo é de 1 a um limite superior definido pelo nível de recurso atual. Para um mapa de cubos, esse valor é 6 vezes o número de mapas de cubo na matriz.|
|**Amostras**|O número de multiamostras por pixel.|

## <a name="graphics-object-viewers"></a>Visualizadores de objeto gráfico
 Para exibir detalhes sobre um objeto, abra-o escolhendo seu nome na tabela de objetos. Detalhes do objeto são exibidos em formatos diferentes, dependendo do tipo do objeto. Por exemplo, as texturas são exibidas usando o Visualizador de textura e o estado do dispositivo, como o contexto do dispositivo D3D11, é exibido como uma lista formatada. Versões diferentes do Direct3D fazem uso de diferentes objetos, e geralmente há visualizadores específicos para os objetos mais importantes de cada versão.

 Aqui está o Visualizador de textura que mostra o conteúdo do estágio de pipeline de fusão de saída.

 ![A visualização de textura exibindo a mesclagem de saída](media/gfx_diag_texture_preview.png "gfx_diag_texture_preview")

### <a name="d3d12-command-list"></a>Lista de comandos do D3D12
 No Direct3D 12, uma lista de comandos é um objeto que registra comandos em um alocador de comando para que eles possam ser enviados para a GPU como uma única solicitação. As listas de comandos geralmente executam uma série de comandos de configuração de estado, desenho, limpar e copiar. Elas são particularmente importantes porque são o método preferencial de renderização no Direct3D 12 e podem ser usadas novamente entre quadros para ajudar a aumentar o desempenho. Os detalhes da lista de comandos são exibidos em uma nova janela de documento, com informações relacionadas a cada estágio de pipeline apresentada em sua própria guia.

### <a name="d3d12-pipeline-state-object-pso"></a>Objeto de estado de pipeline D3D12 (PSO)
 No Direct3D 12, um objeto de estado de pipeline representa uma parte significativa do estado da GPU, incluindo todos os sombreadores definidos atualmente e determinados objetos de estado de função fixa. Depois de criado, um objeto de estado de pipeline é imutável — um aplicativo só pode alterar a configuração do pipeline ligando um objeto de estado de pipeline diferente. Os detalhes do PSO são exibidos em uma nova janela de documento, com detalhes da configuração do pipeline dispostos hierarquicamente.

### <a name="d3d12-root-signature"></a>Assinatura raiz D3D12
 No Direct3D 12, a assinatura raiz define todos os recursos associados a um pipeline de computação ou gráficos, e vincula as listas de comandos aos recursos que os sombreadores exigem. Normalmente, há uma assinatura raiz para gráficos e outra para computação em um aplicativo. Os detalhes da assinatura raiz são exibidos em uma nova janela de documento, com detalhes da assinatura raiz dispostos hierarquicamente.

### <a name="d3d12-resources"></a>Recursos do D3D12
 No Direct3D 12, os recursos são capturados todos os objetos que fornecem dados ao pipeline de renderização; Isso é diferente de Direct3D11, que definiu muitos objetos específicos para diferentes tipos e dimensões de recursos. Um recurso do Direct3D 12 pode conter dados de textura, dados de vértice, dados de sombreador e muito mais — eles podem até mesmo representar destinos de renderização, como o buffer de profundidade. Os detalhes de um recurso do Direct3D 12 são exibidos em uma nova janela de documento; A análise de gráficos usará o visualizador apropriado para o conteúdo do objeto de recurso se for capaz de determinar seu tipo. Por exemplo, um objeto de recurso que contém dados de textura é exibido usando o Visualizador de textura, assim como um objeto D3D11 Texture2D.

### <a name="device-context-object"></a>Objeto de contexto de dispositivo
 No Direct3D 11 e no Direct3D 10, o objeto de contexto do dispositivo (**contexto do dispositivo D3D11** ou **dispositivo d3d10**) é particularmente importante porque contém as informações de estado mais importantes e vincula a outros objetos de estado que estão definidos no momento. Os detalhes do contexto do dispositivo são exibidos em uma nova janela de documento e cada categoria de informações é apresentada lá em sua própria guia. O contexto do dispositivo é alterado quando um novo evento é selecionado para refletir o estado atual do dispositivo.

### <a name="buffer-object"></a>Objeto de buffer
 Detalhes do objeto de buffer (Buffer D3D11 ou D3D10) são exibidos em uma nova janela de documento que apresenta o conteúdo de buffer em uma tabela e fornece uma interface para alterar como o conteúdo de buffer é exibido. A tabela de **dados do buffer** dá suporte a copiar e colar para que você possa usar outra ferramenta, como por exemplo, o Microsoft Excel, para examinar seu conteúdo. O conteúdo do buffer é interpretado de acordo com o valor da **formato** caixa de combinação, localizada acima da tabela de **dados do buffer**. Na caixa, você pode inserir um formato de dados compostos que consiste em tipos de dados listados na tabela a seguir. Por exemplo, "float int" exibe uma lista de estruturas que contêm um valor de ponto flutuante de 32 bits seguido por um valor inteiro com sinal de 32 bits. Formatos de dados compostos que você especificou são adicionados à caixa de combinação para uso posterior.

 Você também pode alternar a caixa de seleção **Mostrar deslocamentos** para ocultar ou exibir o deslocamento de cada elemento no buffer.

|Digite|Descrição|
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
- [Passo a passo: objetos ausentes devido ao estado do dispositivo](walkthrough-missing-objects-due-to-device-state.md)