---
title: Edições sem suporte no Visual Basic editar e continuar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], unsupported method and property body edits
ms.assetid: 9b8fdc41-a193-49ad-ad72-dfcadd46f4b3
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94a151a7adab5c8246cec38c2e62d76788beb6e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155442"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Edições não suportadas em Editar e Continuar do Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editar e Continuar permite parar a execução do programa no modo de interrupção, fazer alterações no código de execução e retomar a execução do programa com as alterações recém-inseridas. As edições declarativas de código que afetam a estrutura pública de uma classe são proibidas em geral, mas muitas edições que você pode fazer em um método, corpo da propriedade ou declarações privadas dentro de uma classe são permitidas.  
  
 Se você precisar fazer uma alteração que não tem suporte, deverá parar a depuração, fazer as alterações e iniciar uma nova sessão de depuração.  
  
### <a name="method-and-property-body-edits"></a><a name="BKMK_MethodandPropertyBodyEdits"></a> Edições do método e do corpo da propriedade  
 **Alterações sem suporte em variáveis locais estáticas**: Adicionar ou atualizar uma variável local ou remover uma variável local estática se isso causar um erro de compilação.  
  
 **Alterações sem suporte em genéricos**: não há suporte para alterações no próprio método genérico ou no corpo do método genérico. A instanciação de um tipo genérico ou chamadas para os métodos genéricos existentes pode ser adicionada, excluída ou modificada.  
  
 **Outras alterações sem suporte**  
  
- Alterando a instrução de invocação de um método que está na pilha de chamadas.  
  
- Adicionando um bloco `Try...Catch`, quando o ponteiro de instrução acabar no bloco `Catch` ou `Finally`.  
  
- Removendo um `Try...Catch` bloco, quando o ponteiro de instrução está em um `Catch` bloco ou `Finally` bloco.  
  
- Adicionando um bloco `Using` em torno do ponteiro de instrução atual.  
  
- Adicionando um bloco `SynchLock` em torno do ponteiro de instrução atual.  
  
### <a name="attribute-edits"></a><a name="BKMK_AttributeEdits"></a> Edições de atributo  
 Editar e Continuar não dá suporte a atributos de modificação. Especificamente, Editar e Continuar não dá suporte às seguintes alterações:  
  
- Definindo, editando ou excluindo uma classe de atributo.  
  
- Adicionando um atributo.  
  
- Editando ou removendo um atributo existente.  
  
### <a name="class-declaration-edits"></a><a name="BKMK_ClassDeclarationEdits"></a> Edições de declaração de classe  
 A maioria das alterações às declarações de classe não são permitidas por Editar e Continuar enquanto estiver no modo de interrupção. Especificamente, Editar e Continuar não dá suporte às seguintes alterações:  
  
- Renomeando, excluindo ou alterando a herança de uma classe existente.  
  
- Implementando uma nova interface ou removendo a implementação de uma interface.  
  
- Alterando modificadores em uma classe.  
  
- Alterando, adicionando ou removendo o status de `ComClass`.  
  
- Editando qualquer declaração de classe genérica.  
  
### <a name="class-member-declaration-edits"></a><a name="BKMK_ClassMemberDeclarationEdits"></a> Edições de declaração de membro de classe  
 As alterações a declarações de membro são proibidas na maioria dos casos de Editar e Continuar. Por exemplo, você não pode alterar a assinatura ou o nível de acesso de um membro, e não poderá remover os membros completamente se isso causar um erro de compilação. Especificamente, Editar e Continuar não dá suporte às seguintes alterações:  
  
- Sombreando uma variável de membro existente declarando uma variável ou membro global do mesmo nome no bloco recipiente.  
  
- Sombreando uma variável local estática declarando uma nova instância dentro de um bloco.  
  
- Removendo os manipuladores para um evento. Adicionar um manipulador de eventos é permitido.  
  
- Adicionando uma nova propriedade ou método de sobrecarga, a menos que a propriedade ou método seja `Private` e não haja ocorrência do nome em nenhuma instrução ativa.  
  
- Adicionando ou removendo a cláusula `WithEvents` em uma variável de membro.  
  
- Excluindo um membro.  
  
- Alterando uma declaração de propriedade ou método para parar de implementar uma interface.  
  
- Editando qualquer método que usa genéricos.  
  
- Alterando a assinatura ou o tipo de retorno de uma propriedade ou método não privado.  
  
- Substituindo ou sombreando um membro em uma classe base.  
  
- Adicionar um novo campo em qualquer classe marcada com `SequentialLayout` ou `ExplicitLayout` .  
  
- Alterando o status `MustInherit` ou `NotOverridable` de um método.  
  
- Alterando os modificadores de acesso para uma propriedade ou método.  
  
- Alterando o tipo ou status somente leitura de um campo.  
  
- Alterando um campo público.  
  
### <a name="compiler-option-edits"></a><a name="BKMK_CompilerOptionEdits"></a> Edições da opção do compilador  
 Ao usar Editar e Continuar no modo de interrupção, você não poderá alterar, adicionar ou remover as seguintes opções do compilador:  
  
- **Opção Estrita**  
  
- **Opção Explícita**  
  
- **Opção Comparar**  
  
### <a name="constants-edits"></a><a name="BKMK_ConstantsEdits"></a> Edições de constantes  
 As alterações a constantes enquanto estiver no modo Editar e Continuar são muito limitadas. Especificamente, Editar e Continuar não dá suporte às seguintes alterações:  
  
- Adicionando ou atualizando uma variável constante.  
  
- Alterando o tipo ou o valor de uma constante.  
  
- Removendo uma constante.  
  
### <a name="delegate-and-event-declaration-edits"></a><a name="BKMK_DelegateandEventDeclarationEdits"></a> Edições de declaração de evento e delegate  
 Algumas alterações em delegados e eventos não são permitidas por editar e continuar durante o modo de interrupção. Especificamente, Editar e Continuar não dá suporte às seguintes alterações:  
  
- Modificando ou excluindo uma definição de representante.  
  
- Excluindo um evento.  
  
### <a name="enumeration-edits"></a><a name="BKMK_EnumerationEdits"></a> Edições de enumeração  
 As alterações a enumerações (`Enums`) não são permitidas por Editar e Continuar durante o modo de interrupção. Especificamente, Editar e Continuar não dá suporte às seguintes alterações:  
  
- Modificando o tipo subjacente de um `Enum`.  
  
- Alterando, adicionando ou removendo um membro `Enum`.  
  
- Alterando o modificador de um `Enum`.  
  
### <a name="external-declarations-edits"></a><a name="BKMK_ExternalDeclarationsEdits"></a> Edições de declarações externas  
 Em geral, você não pode alterar as declarações de métodos externos durante Editar e Continuar. Especificamente, Editar e Continuar não dá suporte às seguintes alterações:  
  
- Adicionando ou removendo uma declaração externa.  
  
- Alterando a assinatura ou atributos de marshaling de uma declaração externa.  
  
### <a name="imports-edits"></a><a name="BKMK_ImportsEdits"></a> Imports edições  
 Editar e Continuar não permite adicionar, modificar ou remover instruções `Imports` quando está em modo de interrupção.  
  
### <a name="interface-definition-edits"></a><a name="BKMK_InterfaceDefinitionEdits"></a> Edições de definição de interface  
 Embora frequentemente você tenha permissão de fazer alterações nos membros que implementam interfaces, as alterações a definições de interface reais geralmente não são permitidas por Editar e Continuar. Especificamente, Editar e Continuar não dá suporte às seguintes alterações:  
  
- Alterando, adicionando ou removendo membros de interface.  
  
- Excluindo uma interface existente.  
  
- Alterando o modificador de uma interface.  
  
- Alterando a hierarquia de herança da interface.  
  
### <a name="module-declaration-edits"></a><a name="BKMK_ModuleDeclarationEdits"></a> Edições de declaração de módulo  
 A maioria das alterações às declarações de módulo não são permitidas por Editar e Continuar enquanto estiver no modo de interrupção. Especificamente, Editar e Continuar não dá suporte às seguintes alterações:  
  
- Criando um novo módulo.  
  
- Renomeando ou excluindo um módulo existente.  
  
- Alterando o modificador de acesso para um módulo.  
  
### <a name="module-member-declaration-edits"></a><a name="BKMK_ModuleMemberDeclarationEdits"></a> Edições de declaração de membro de módulo  
 Usando Editar e Continuar, você pode executar uma variedade de alterações a membros do módulo, como propriedades, métodos e campos, quando estiver em modo de interrupção. Algumas alterações, porém, não têm suporte. Mais notavelmente, editar e continuar não dá suporte à adição, exclusão ou alteração do tipo ou assinatura de qualquer membro.  
  
 Especificamente, Editar e Continuar não dá suporte às seguintes alterações:  
  
- Adicionar um novo membro a menos que não haja nenhuma ocorrência do nome em nenhuma instrução ativa.  
  
- Removendo uma propriedade ou método.  
  
- Alterando a assinatura de uma propriedade ou método.  
  
- Adicionar, renomear, mover ou excluir um campo.  
  
- Editando qualquer método que usa genéricos.  
  
- Alterando os modificadores de acesso para uma propriedade ou método, por exemplo, alterar `Public` para `Private`.  
  
- Excluindo ou alterando o tipo de um campo existente.  
  
### <a name="nested-type-declaration-edits"></a><a name="BKMK_NestedTypeDeclarationEdits"></a> Edições de declaração de tipo aninhado  
 Editar e continuar não dá suporte à movimentação de um tipo aninhado para outro namespace ou tipo.  
  
### <a name="structure-declaration-edits"></a><a name="BKMK_StructureDeclarationEdits"></a> Edições da declaração de estrutura  
 A maioria das alterações em declarações de estrutura não é permitida por editar e continuar enquanto estiver no modo de **interrupção** . Especificamente, Editar e Continuar não dá suporte às seguintes alterações:  
  
- Renomeando ou excluindo uma estrutura existente.  
  
- Implementando uma nova interface ou removendo a implementação de uma interface.  
  
- Alterando o modificador de acesso para uma estrutura.  
  
### <a name="structure-member-declaration-edits"></a><a name="BKMK_StructureMemberDeclarationEdits"></a> Edições de declaração de membro de estrutura  
 Usando Editar e Continuar, você pode executar uma variedade de alterações a membros da estrutura (propriedades, métodos e campos), quando estiver em modo de interrupção. Algumas alterações, porém, não têm suporte, especialmente as alterações que afetam a declaração de membros da estrutura. Especificamente, Editar e Continuar não dá suporte às seguintes alterações:  
  
- Removendo uma propriedade ou método.  
  
- Adicionando ou removendo um campo.  
  
- Alterando a assinatura de uma propriedade ou método.  
  
- Editando qualquer método que usa genéricos.  
  
- Alterando se uma declaração de propriedade ou método implementam uma interface.  
  
- Alterar os modificadores de acesso de uma propriedade ou método (por exemplo, alterar `Public` para **privado**).  
  
- Removendo um campo.  
  
- Alterando o tipo de um campo.  
  
## <a name="see-also"></a>Consulte Também  
 [Como: aplicar edições no modo de interrupção com editar e continuar](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [Editar e Continuar (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
