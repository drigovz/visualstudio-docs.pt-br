---
title: Recursos em VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 493e9834e3d7cf6d82cebb8dd93d5369678c7be0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705595"
---
# <a name="resources-in-vspackages"></a>Recursos em VSPackages
Você pode incorporar recursos localizados em DLLs de satélite nativo, DLLs de satélite gerenciados ou em um VSPackage gerenciado.

 Alguns recursos não podem ser incorporados em VSPackages. Os seguintes tipos gerenciados podem ser incorporados:

- Cadeias de caracteres

- Teclas de carga do pacote (que também são strings)

- Ícones da janela da ferramenta

- Arquivos CTO (Command Table Output, saída de tabela de comando compiladas)

- Bitmaps do CTO

- Ajuda de linha de comando

- Sobre dados da caixa de diálogo

  Os recursos em um pacote gerenciado são selecionados por iD de recurso. Uma exceção é o arquivo CTO, que deve ser chamado CTMENU. O arquivo CTO deve aparecer na `byte[]`tabela de recursos como a . Todos os outros itens de recurso são identificados por tipo.

  Você pode <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> usar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] atributo para indicar que os recursos gerenciados estão disponíveis.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  A <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> configuração desta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] maneira indica que deve ignorar DLLs de satélite não <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>gerenciados quando ele procura recursos, por exemplo, usando . Se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] encontrar dois ou mais recursos que tenham o mesmo ID de recurso, ele usará o primeiro recurso encontrado.

## <a name="example"></a>Exemplo
 O exemplo a seguir é uma representação gerenciada de um ícone de janela de ferramenta.

```
<data name="1001"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyToolWinIcon.bmp;
     System.Drawing.Bitmap,
     System.Drawing,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

 O exemplo a seguir demonstra como incorporar a matriz de bytes CTO, que deve ser chamada CTMENU.

```
<data name="CTMENU"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyPackage.cto;
     System.Byte[],
     mscorlib,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

## <a name="implementation-notes"></a>Notas de implementação
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]atrasa o carregamento de VSPackages sempre que possível. Uma conseqüência de incorporar um arquivo CTO [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] em um VSPackage é que deve carregar todos esses VSPackages na memória durante a configuração, que é quando ele constrói uma tabela de comando mesclada. Os recursos podem ser extraídos de um VSPackage examinando os metadados sem executar código no VSPackage. O VSPackage não é inicializado no momento, então a perda de desempenho é mínima.

 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] solicita um recurso de um VSPackage após a configuração, é provável que esse pacote já esteja carregado e inicializado, de modo que a perda de desempenho é mínima.

## <a name="see-also"></a>Confira também
- [Gerenciar VSPackages](../../extensibility/managing-vspackages.md)
- [Recursos localizados em aplicativos MFC: DLLs satélites](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
