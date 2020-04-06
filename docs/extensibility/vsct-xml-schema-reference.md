---
title: Referência do esquema VSCT XML | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 923a0c4b64fcae3a409a2298d6d481f6e1bb14db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697918"
---
# <a name="vsct-xml-schema-reference"></a>Referência de esquema VSCT XML
Fornece uma tabela de elementos do esquema do compilador de tabela de comando, com elementos e atributos infantis permitidos para cada um.

 Um arquivo de configuração de tabela de comando baseado em XML (.vsct) define os elementos de comando que um VSPackage fornece ao ambiente de desenvolvimento integrado (IDE). Esses elementos incluem itens de menu, menus, barras de ferramentas e caixas de combinação.

> [!NOTE]
> O compilador VSCT pode executar um pré-processador no arquivo .vsct. Como este é tipicamente o pré-processador C++, você pode definir inclui e macros que têm a mesma sintaxe que é usada em arquivos C++. Exemplos disso são fornecidos no arquivo .vsct que o assistente **do Novo Projeto** cria para um projeto VSPackage.

## <a name="optional-elements"></a>Elementos opcionais
 Alguns elementos VSCT são opcionais. Se `Parent` um argumento não for especificado, Group_Undefined:0 será implícito. Se `Icon` um argumento não for especificado, guidOfficeIcon:msotcidNoIcon estará implícito. Quando uma tecla de atalho é definida, a emulação, que normalmente não é utilizada, é opcional.

 Os itens do Bitmap podem ser incorporados na hora da compilação, especificando a localização da tira bitmap no `href` argumento. A tira bitmap é copiada durante a mesclagem em vez de extraída dos recursos da DLL. Quando `href` um argumento é `usedList` fornecido, o argumento se torna opcional, e todos os slots na tira bitmap são considerados usados.

 Todos os valores GUID e ID devem ser definidos usando nomes simbólicos. Esses nomes podem ser definidos em \<arquivos de cabeçalho ou em seções de> de símbolos VSCT. Os nomes simbólicos devem \<ser locais, incluídos \<através de incluir elementos>, ou referenciados por elementos> Extern. Um nome simbólico é importado de um \<arquivo de cabeçalho especificado em um elemento extern> se ele seguir o padrão simples de #define VALOR SÍMBOLO. O valor pode ser outro símbolo desde que esse símbolo tenha sido previamente definido. As definições GUID devem seguir o formato OLE ou C++. Os valores de Identificação podem ser dígitos decimais ou dígitos hexadecimais precedidos por 0x, como mostrado nas seguintes linhas:

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }

  Comentários XML podem ser usados, mas ferramentas de interface gráfica de ida e volta (GUI) podem descartá-los. O conteúdo \<de Elementos de Anotação> é garantido para ser mantido independentemente do formato.

## <a name="schema-hierarchy"></a>Hierarquia de esquemas
 Um arquivo .vsct tem os seguintes elementos principais.

- [Elemento CommandTable](../extensibility/commandtable-element.md)

- [Elemento extern](../extensibility/extern-element.md)

- [Incluir elemento](../extensibility/include-element.md)

- [Definir elemento](../extensibility/define-element.md)

- [Elemento comandos](../extensibility/commands-element.md)

- [Elemento ComandosDe posicionamento](../extensibility/commandplacements-element.md)

- [Elemento de restrições de visibilidade](../extensibility/visibilityconstraints-element.md)

- [Elemento KeyBindings](../extensibility/keybindings-element.md)

- [Elemento UsedCommands](../extensibility/usedcommands-element.md)

- [Elemento pai](../extensibility/parent-element.md)

- [Elemento ícone](../extensibility/icon-element.md)

- [Elemento cordas](../extensibility/strings-element.md)

- [Elemento Bandeira de Comando](../extensibility/command-flag-element.md)

- [Elemento símbolos](../extensibility/symbols-element.md)

- [Atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Confira também
- [Como o VSPackages adiciona elementos de interface de usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Roteamento de comando em VSPacotes](../extensibility/internals/command-routing-in-vspackages.md)
