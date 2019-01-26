---
title: 'Como: Definir atributos CLR em um elemento'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 54b4340fe72552f3287a5c6ebec55c9c9d326ac1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932266"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Como: Definir atributos CLR em um elemento
Atributos personalizados são atributos especiais que podem ser adicionados a diagramas, formas, conectores e elementos de domínio. Você pode adicionar qualquer atributo que herda o `System.Attribute` classe.

### <a name="to-add-a-custom-attribute"></a>Para adicionar um atributo personalizado

1.  No **Gerenciador de DSL**, selecione o elemento ao qual você deseja adicionar um atributo personalizado.

2.  No **propriedades** janela, ao lado de **atributos personalizados** propriedade, clique no botão Procurar (**...** ) ícone.

     O **editar atributos** caixa de diálogo é aberta.

3.  No **nome** coluna, clique em  **\<Adicionar atributo >** e digite o nome do seu atributo. Pressione ENTER.

4.  A linha sob o nome do atributo mostra parênteses. Nessa linha, digite um tipo de parâmetro para o atributo (por exemplo, `string`), e pressione ENTER.

5.  No **nome da propriedade** coluna, digite um nome apropriado, por exemplo, `MyString`.

6.  Clique em **OK**.

     O **atributos personalizados** propriedade agora exibe o atributo no seguinte formato:

     `[` *AttributeName* `(` *ParameterName* `=` *Type* `)]`

## <a name="see-also"></a>Consulte também

- [Glossário de ferramentas de linguagem específica do domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)