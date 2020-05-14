---
title: Inicialização do designer e configuração de metadados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e876dd9e6fa95bbe180d1737bc8c4911f16e1e9a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712221"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicialização do designer e configuração de metadados

A manipulação dos atributos de metadados e filtros associados a um componente de designer ou <xref:System.Type> designer fornece um mecanismo para que as aplicações definam quais ferramentas são usadas por um determinado designer para lidar com diferentes objetos (como estruturas de dados, classes ou entidades gráficas), quando o designer está disponível e como o Visual Studio IDE está configurado para suportar o designer (por exemplo, qual categoria ou guia de **caixa de ferramentas** está disponível).

O [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornece vários mecanismos para facilitar o controle da inicialização de um designer ou componente designer e a manipulação de seus metadados por um VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Inicialize metadados e informações de configuração
 Como eles são carregados sob demanda, os VSPackages podem não ter sido carregados pelo ambiente do Visual Studio antes da instanciação de um designer. Portanto, o VSPackages não pode usar o mecanismo padrão para configurar um <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> componente designer ou designer na criação, que é lidar com um evento. Em vez disso, um VSPackage <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> implementa uma instância da interface e registra-se para fornecer personalizações, chamadas de extensões de superfície de design.

### <a name="customize-initialization"></a>Personalizar a inicialização

Personalizar um designer, um componente ou uma superfície de designer envolve:

1. Modificando os metadados do designer e <xref:System.Type> alterando efetivamente como um certo é acessado ou convertido.

    Isso é normalmente <xref:System.Drawing.Design.UITypeEditor> feito <xref:System.ComponentModel.TypeConverter> através dos mecanismos ou.

    Por exemplo, <xref:System.Windows.Forms>quando os designers baseados são inicializados, o ambiente Visual Studio modifica o <xref:System.Drawing.Design.UITypeEditor> para <xref:System.Web.UI.WebControls.Image> objetos usados com o designer para usar o gerenciador de recursos para obter bitmaps em vez do sistema de arquivos.

2. Integrar-se ao ambiente, por exemplo, assinando eventos ou obtendo informações de configuração do projeto. Você pode obter informações de configuração <xref:System.ComponentModel.Design.ITypeResolutionService> do projeto e se inscrever em eventos obtendo a interface.

3. Modificação do ambiente do usuário ativando categorias apropriadas **da Caixa de Ferramentas** ou restringindo <xref:System.ComponentModel.ToolboxItemFilterAttribute> a aplicabilidade do designer aplicando uma instância da classe ao designer.

### <a name="designer-initialization-by-a-vspackage"></a>Inicialização do designer por um VSPackage

Um VSPackage deve lidar com a inicialização do designer por:

1. Criando um objeto <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> implementando a classe.

   > [!NOTE]
   > A <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe nunca deve ser implementada <xref:Microsoft.VisualStudio.Shell.Package> no mesmo objeto que a classe.

2. Registrando a classe <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> que implementa como suporte para as extensões de designer do VSPackage. Registre a classe aplicando <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>instâncias <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> de , e para a classe <xref:Microsoft.VisualStudio.Shell.Package>que fornece a implementação do VSPackage de .

Sempre que um componente de designer ou designer é criado, o ambiente visual studio:

- Acessa cada provedor de extensão de superfície de projeto registrado.

- Instancia e inicializa uma instância do objeto <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> de cada provedor de extensão de superfície de projeto.

- Chama o método ou <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> método de cada provedor de extensão de superfície de projeto (conforme apropriado).

Ao implementar <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> o objeto como membro de um VSPackage, é importante entender que:

- O ambiente Visual Studio não fornece nenhum controle sobre quais `DesignSurfaceExtension` metadados ou outras configurações as configurações de um determinado provedor modifica. É possível para dois `DesignSurfaceExtension` ou mais provedores modificar o mesmo recurso de designer de formas conflitantes, com a modificação final sendo definitiva. É indeterminado qual modificação é aplicada pela última vez.

- É possível restringir explicitamente a implementação <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> do objeto a designers <xref:System.ComponentModel.ToolboxItemFilterAttribute> específicos aplicando instâncias de essa implementação. Para obter mais informações sobre a filtragem <xref:System.ComponentModel.ToolboxItemFilterType>de itens da Caixa de **Ferramentas,** consulte o <xref:System.ComponentModel.ToolboxItemFilterAttribute> e .

## <a name="additional-metadata-provisioning"></a>Provisionamento adicional de metadados

Um VSPackage pode alterar a configuração de um componente de designer ou designer que não seja na hora do design.

A <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe pode ser usada programáticamente ou aplicada a um VSPackage que fornece um designer.

Uma instância <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> da classe é usada para modificar os metadados dos componentes criados em uma superfície de projeto. Por exemplo, pode-se substituir um <xref:System.Windows.Forms.CommonDialog> navegador de propriedade padrão usado por objetos por um navegador de propriedade personalizado.

As modificações fornecidas <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> por uma instância aplicada à <xref:Microsoft.VisualStudio.Shell.Package> implementação de um VSPackage podem ter um dos dois escopos:

- Global - para todas as novas instâncias de um determinado componente

- Local - pertencente apenas à instância do componente criado em uma superfície de design fornecida pelo VSPackage atual.

A `IsGlobal` propriedade <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> da instância aplicada à implementação <xref:Microsoft.VisualStudio.Shell.Package> de um VSPackage determina esse escopo.

Aplicar o atributo a <xref:Microsoft.VisualStudio.Shell.Package> uma <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> implementação <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> de `true`com a propriedade do objeto definido para , como abaixo, altera o navegador para todo o ambiente do Visual Studio:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Se a bandeira global `false`foi definida para , então a alteração de metadados será local para o designer atual suportado pelo VSPackage atual:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> A superfície de projeto só suporta a criação de componentes e, portanto, apenas componentes podem ter metadados locais. No exemplo acima, estávamos tentando modificar uma propriedade, como a `Color` propriedade de um objeto. Se `false` fosse aprovada para a `CustomBrowser` bandeira global, nunca apareceria `Color`porque o designer nunca cria uma instância de . Definir a bandeira `false` global é útil para componentes, como controles, temporizadores e caixas de diálogo.

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Estender o suporte ao tempo de projeto](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
