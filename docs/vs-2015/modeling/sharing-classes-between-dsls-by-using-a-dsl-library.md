---
title: Compartilhando Classes entre DSLs por meio de uma biblioteca de DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1f5b12dce533aa03cf12efd8a6f9fc26ce990e5d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073820"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Compartilhando classes entre DSLs por meio de uma biblioteca de DSLs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK de modelagem e visualização, você pode criar uma definição de DSL incompleta que você pode importar para outra DSL. Isso permite fatorar partes comuns dos modelos semelhantes.  
  
## <a name="creating-and-using-dsl-libraries"></a>Criando e usando bibliotecas de DSL  
  
#### <a name="to-create-a-dsl-library"></a>Para criar uma biblioteca de DSL  
  
1. Criar um novo projeto DSL e escolher o modelo de solução de biblioteca de DSL.  
  
     Um único projeto DSL será criado com um modelo vazio.  
  
2. Você pode adicionar classes de domínio, relações, formas e assim por diante.  
  
     Os elementos na biblioteca não é necessário que formar uma única árvore de incorporação.  
  
     Para definir uma relação de importadores podem usar, crie duas classes de domínio e criar a relação entre eles.  
  
     Considere definir a **modificador de herança** das classes de domínio para `Abstract`.  
  
3. Você pode adicionar elementos que você define no DSL Explorer, como construtores de Conexão.  
  
4. Você pode adicionar as personalizações que requerem código adicional, como restrições de validação.  
  
5. Clique em **transformar todos os modelos**.  
  
6. Compile o projeto.  
  
7. Quando você distribui a DSL para que outras pessoas usem, você deve fornecer o assembly compilado (DLL) e o arquivo `DslDefinition.dsl`. Você pode encontrar o assembly compilado em uma pasta sob `Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>Para importar uma biblioteca de DSL  
  
1. Em outra definição de DSL, em **Gerenciador de DSL**, clique com botão direito a classe raiz do DSL e, em seguida, clique em **adicionar uma nova importação de DslLibrary**.  
  
2. Na janela Propriedades, defina as **caminho do arquivo** da biblioteca. Você pode usar um caminho absoluto ou relativo.  
  
    A biblioteca importada aparece no Gerenciador de DSL, no modo somente leitura.  
  
3. Você pode usar as classes importadas como classes base. Criar uma classe de domínio na importação DSL e nas propriedades da janela, defina **base de dados de classe** para uma classe importada.  
  
4. Clique em transformar todos os modelos.  
  
5. Para o projeto DSL, adicione uma referência ao assembly (DLL) que foi criado pelo projeto de biblioteca de DSL.  
  
6. Compile a solução.  
  
   Uma biblioteca de DSL podem importar outras bibliotecas. Quando você importa uma biblioteca, suas importações automaticamente também aparecem no Gerenciador de DSL.  
  
## <a name="see-also"></a>Consulte também  
 [Como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md)
