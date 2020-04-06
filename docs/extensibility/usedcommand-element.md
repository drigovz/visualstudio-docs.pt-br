---
title: Elemento UsedCommand | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65030c3fe24c3456b0c4c99a667362d2a4c67703
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698832"
---
# <a name="usedcommand-element"></a>Elemento UsedCommand
Habilita um VSPackage para acessar um comando definido em outro arquivo .vsct. Por exemplo, se o vsPackage usar o comando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **'Copiar** padrão', que é definido pelo shell, você pode adicionar o comando a um menu ou barra de ferramentas sem implementá-lo.

## <a name="syntax"></a>Sintaxe

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|guid|Obrigatórios. O GUID do par GUID ID que identifica o comando.|
|id|Obrigatórios. O ID do par GUID ID que identifica o comando.|
|Condição|Opcional. Ver [Atributos Condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|Nenhum||

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Grupos usadosComando comandos e outros agrupamentos usedCommands.|

## <a name="remarks"></a>Comentários
 Ao adicionar um `<UsedCommands>` comando ao elemento, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] um VSPackage informa ao ambiente que o VSPackage requer o comando. Você deve `<UsedCommand>` adicionar um elemento para qualquer comando que seu pacote exija que possa não ser incluído em todas as versões e configurações do Visual Studio. Por exemplo, se o pacote chamar um comando específico do Visual C++, o comando não `<UsedCommand>` estará disponível para os usuários do Visual Web Developer, a menos que você inclua um elemento para o comando.

## <a name="example"></a>Exemplo

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Confira também
- [Elemento UsedCommands](../extensibility/usedcommands-element.md)
- [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
