---
title: Estado de gráficos | Microsoft Docs
description: Solucionar problemas de renderização vendo o estado de gráficos para cada chamada de desenho. As partes do estado que foram alteradas da chamada anterior são realçadas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de8f3c356cfe05aade3e4f2197b3f7429967a259
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993999"
---
# <a name="graphics-state"></a>Estado gráfico
A janela de estado no diagnóstico de gráficos do Visual Studio ajuda você a entender o estado de gráficos que está ativo no momento do evento atual, como uma chamada de desenho.

## <a name="understanding-the-state-window"></a>Compreendendo a janela de estado
 A janela estado coleta o estado que afeta a renderização e a apresenta hierarquicamente, em um único lugar. Dependendo da versão do Direct3D que seu aplicativo usa, as informações apresentadas na janela de estado podem ter diferenças.

### <a name="state-views"></a>Modos de exibição de estados
 Você pode exibir a tabela de estado de várias maneiras diferentes:

|Exibir|Descrição|
|----------|-----------------|
|Exibição do estado de entrada da API|Essa exibição apresenta o estado em um layout semelhante aos objetos do Direct3D que compõem o estado.|
|Exibição de estado de entrada lógica|Essa exibição apresenta o estado em uma exibição lógica que não espelha o layout dos objetos do Direct3D que compõem o estado.|
|Exibição de estado fixado|Em vez de uma hierarquia, a exibição de estado fixado apresenta itens de estado fixos em uma lista simples com nomes totalmente qualificados. Essa exibição torna possível exibir muitos itens de estado de diferentes pacotes de estado em um pequeno número de linhas.|

##### <a name="to-change-the-state-view"></a>Para alterar o modo de exibição de estado

- Na janela estado, no canto superior esquerdo, logo abaixo da TitleBar, escolha o botão que corresponde ao estilo de exibição de estado que você deseja usar.

  - **Mostrar exibição de estado de recebimento de API**

  - **Mostrar exibição de estado lógico**

  - **Mostrar exibição de estado fixado**

> [!IMPORTANT]
> Você deve fixar o estado nas exibições **Mostrar estado de entrada da API** ou **Mostrar estado lógico** para que ela seja exibida na **exibição mostrar estado fixado**.

### <a name="state-table-format"></a>Formato de tabela de estado
 A janela de Estado apresenta várias colunas de informações.

|Coluna|Descrição|
|------------|-----------------|
|Nome|O nome do item de estado. Se esse item representar um pacote de estado, o item poderá ser expandido para exibi-lo.<br /><br /> Nos Estados de exibição de **estado de entrada de API** e modo de exibição de **estado lógico** , os nomes são recuados para mostrar a relação hierárquica entre os Estados.<br /><br /> No estado de **exibição de estado fixado** , nomes totalmente qualificados são exibidos em uma lista simples.|
|Valor|O valor do item de estado.|
|Type|O tipo do item de estado.|

### <a name="changed-state"></a>Estado alterado
 O estado de gráficos normalmente muda incrementalmente entre chamadas de desenho subsequentes e muitos tipos de problemas de renderização são causados quando o estado é alterado incorretamente. Para ajudá-lo a descobrir qual estado mudou desde a chamada de desenho anterior, o estado alterado é marcado com um asterisco e exibido em vermelho — isso se aplica não apenas ao estado em si, mas também ao item de estado pai, para que você possa identificar facilmente o estado alterado no nível mais alto e, em seguida, detalhar os detalhes.

### <a name="pinning-state"></a>Estado de fixação
 Como muitos aplicativos renderizam objetos semelhantes sequencialmente, alterando um conjunto conhecido de estado, às vezes é útil fixar os Estados de alteração em vigor para que você possa observar como ele muda à medida que você passa da chamada de desenho para chamada de desenho.

 Isso também pode ser útil se você tiver isolado a origem de um problema devido a uma alteração em um estado específico.

##### <a name="to-pin-state-in-place"></a>Para fixar o estado no local

1. Na janela estado, localize o estado em que você está interessado. Talvez seja necessário expandir o estado de nível superior para localizar os detalhes nos quais você está interessado.

2. Coloque o cursor sobre o estado em que você está interessado. Um ícone de pino aparece à esquerda do item de estado.

3. Escolha o ícone de pino para fixar o item de estado no local.
