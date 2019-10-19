---
title: Visão geral da interface do usuário das Ferramentas de Linguagem Específica de Domínio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bffb1f7fe6449f078c21c14b0a070cbd23db539
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652133"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Visão geral da interface de usuário das Ferramentas de Linguagem Específica do Domínio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando você abrir uma solução de Ferramentas DSL (Ferramentas de Linguagem Específica de Domínio) no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pela primeira vez, a interface do usuário será semelhante à figura a seguir.

 ![Designer de DSL](../modeling/media/dsl-designer.png "|::ref1::|")

 A tabela a seguir explica como as partes da interface do usuário são usadas.

|**Elemento**|**Definição**|
|-----------------|--------------------|
|Diagrama|O diagrama exibe o modelo de domínio.<br /><br /> O diagrama tem dois lados. Um dos lados define os tipos dos elementos nos modelos. O outro lado define como os modelos aparecerão na tela.|
|Caixa de Ferramentas|Arraste as ferramentas da caixa de ferramentas para adicionar classes de domínio e tipos de forma ao diagrama. Para adicionar relacionamentos, conectores e mapas de formas, clique na ferramenta, em seguida, clique no nó de origem no diagrama e, em seguida, no nó de destino.|
|DSL Explorer|O **Gerenciador de DSL** é exibido quando uma definição de DSL é a janela ativa. Ele mostra a DSL como uma árvore. O Gerenciador de DSL permite editar os recursos do modelo que não são exibidos no diagrama. Por exemplo, você pode adicionar itens de caixa de ferramentas e ativar o processo de validação usando o **Gerenciador de DSL**.|
|Janela Detalhes de DSL|A janela **Detalhes de DSL** mostra as propriedades dos elementos do modelo de domínio que permitem que você controle como os elementos são exibidos e como eles são copiados e excluídos.<br /><br /> – Por padrão, a janela **Detalhes de DSL** aparece ao lado das janelas **Lista de Erros** e **Saída**.|

## <a name="the-domain-model-diagram"></a>O diagrama de modelo de domínio
 O diagrama de modelo de domínio é dividido em duas partes. Um dos lados do diagrama mostra os elementos e os relacionamentos no modelo. O outro lado mostra como o modelo deve ser exibido e inclui as formas que serão usadas para exibir os elementos e as propriedades do diagrama de modelo. A imagem a seguir mostra os elementos do diagrama.

 ![Designer de DSL com raia](../modeling/media/dsl-desinger.png "|::ref2::|")

 A tabela a seguir explica alguns dos elementos do diagrama de modelo de domínio.

|**Prazo**|**Definição**|
|--------------|--------------------|
|Classe de domínio|As classes de domínio são os tipos de elementos em seus modelos.<br /><br /> Uma classe de domínio pode aparecer mais de uma vez em um diagrama, se ela for o destino de mais de um relacionamento.<br /><br /> Para adicionar uma classe de domínio, arraste a ferramenta de classe de domínio da **Caixa de ferramentas** para o lado **Classes e relacionamentos** do diagrama.|
|Relacionamento de domínio|Os relacionamentos de domínio são os tipos de links entre os elementos nos modelos.<br /><br /> Um *relacionamento de incorporação* indica que o elemento de destino pertence ou está contido no elemento de origem e aparece como uma linha sólida. Cada elemento em um modelo deve ser o destino de um relacionamento de incorporação, para que o modelo forme uma árvore. Um *relacionamento de referência* indica um link geral entre elementos de modelo e aparece como uma linha tracejada. Qualquer elemento pode ter qualquer número de links de referência.<br /><br /> Crie um relacionamento clicando na ferramenta na **Caixa de ferramentas** e clicando na classe de domínio de origem e, em seguida, na classe de destino.|
|Formas e Conectores|As formas especificam como os elementos de modelo devem ser exibidos em um diagrama DSL, os conectores especificam as linhas em um diagrama de DSL que podem ser usadas para exibir relacionamentos.<br /><br /> Para criar uma forma ou um conector, arraste a ferramenta para o lado **Elementos de Diagrama** do diagrama.|
|Mapas de formas|Um mapa de formas aparece como uma linha no diagrama de modelo de domínio, uma vinculando uma forma à classe de domínio que ele exibe ou um conector com o relacionamento de domínio que ele exibe.|

## <a name="see-also"></a>Veja também
 [Visão geral de Ferramentas de Linguagem Específica de Domínio](../modeling/overview-of-domain-specific-language-tools.md) [ferramentas de linguagem específica de domínio Glossário](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md)
