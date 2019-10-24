---
title: Elemento UsedCommand | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ea8f27cafb166968f66c53dc68398526e0aa5d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718782"
---
# <a name="usedcommand-element"></a>Elemento UsedCommand
Permite que um VSPackage acesse um comando que é definido em outro arquivo. vsct. Por exemplo, se o VSPackage usar o comando de **cópia** padrão, que é definido pelo shell [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você poderá adicionar o comando a um menu ou barra de ferramentas sem implementá-lo novamente.

## <a name="syntax"></a>Sintaxe

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|Volume|Necessário. O GUID do par de IDs de GUID que identifica o comando.|
|id|Necessário. A ID do par de IDs de GUID que identifica o comando.|
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|Nenhum||

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Agrupa elementos UsedCommand e outros agrupamentos do UsedCommands.|

## <a name="remarks"></a>Comentários
 Ao adicionar um comando ao elemento `<UsedCommands>`, um VSPackage informa ao ambiente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que o VSPackage requer o comando. Você deve adicionar um elemento `<UsedCommand>` para qualquer comando que seu pacote exigir que talvez não seja incluído em todas as versões e configurações do Visual Studio. Por exemplo, se o pacote chamar um comando específico do Visual C++, o comando não estará disponível para os usuários do Visual Web Developer, a menos que você inclua um elemento `<UsedCommand>` para o comando.

## <a name="example"></a>Exemplo

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Consulte também
- [Elemento UsedCommands](../extensibility/usedcommands-element.md)
- [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)