---
title: 'Como: Definir atributos CLR em um elemento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 54c3bd854f824818d9656a33ccf30391f750a491
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080716"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Como: Definir atributos CLR em um elemento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Atributos personalizados são atributos especiais que podem ser adicionados a diagramas, formas, conectores e elementos de domínio. Você pode adicionar qualquer atributo que herda o `System.Attribute` classe.  
  
### <a name="to-add-a-custom-attribute"></a>Para adicionar um atributo personalizado  
  
1. No **Gerenciador de DSL**, selecione o elemento ao qual você deseja adicionar um atributo personalizado.  
  
2. No **propriedades** janela, ao lado de **atributos personalizados** propriedade, clique no botão Procurar (**...** ) ícone.  
  
     O **editar atributos** caixa de diálogo é aberta.  
  
3. No **nome** coluna, clique em  **\<Adicionar atributo >** e digite o nome do seu atributo. Pressione ENTER.  
  
4. A linha sob o nome do atributo mostra parênteses. Nessa linha, digite um tipo de parâmetro para o atributo (por exemplo, `string`), e pressione ENTER.  
  
5. No **nome da propriedade** coluna, digite um nome apropriado, por exemplo, `MyString`.  
  
6. Clique em **OK**.  
  
     O **atributos personalizados** propriedade agora exibe o atributo no seguinte formato:  
  
     `[` *AttributeName* `(` *ParameterName* `=` *Type* `)]`  
  
## <a name="see-also"></a>Consulte também  
 [Glossário das Ferramentas de Linguagem Específica de Domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
