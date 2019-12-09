---
title: Empacotando informações de implantação & em itens de projeto
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: db805c308fd245554824997b24236eb2e2d80e62
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984209"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Fornecer informações de empacotamento e implantação em itens de projeto
  Todos os itens de projeto do SharePoint em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] têm propriedades que você pode usar para fornecer dados adicionais quando o projeto é implantado no SharePoint. Estas são as seguintes propriedades:

- Propriedades do recurso

- Receptores de recursos

- Referências de saída do projeto

- Entradas de controle seguro

  Essas propriedades aparecem na janela **Propriedades** .

## <a name="feature-properties"></a>Propriedades do recurso
 Use a propriedade **Propriedades do recurso** para especificar os dados que o recurso usa. Os dados de propriedades de recurso são um conjunto de valores (armazenados como pares de chave/valor) que é incluído com um recurso quando ele é implantado no SharePoint. Depois que o recurso for implantado, você poderá acessar os valores de propriedade em seu código.

 Quando você adiciona um valor de propriedade de recurso a um item de projeto, o valor é adicionado como um elemento no manifesto do recurso do item. Em um projeto de modelo BDC (conectividade de dados corporativos), por exemplo, a propriedade de recurso ModelFileName aparece como:

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 Depois de definir um valor de propriedade de recurso, ele é adicionado como um elemento FeatureProperty no arquivo *. COMDATA* do projeto. Para obter informações sobre como acessar as propriedades no SharePoint, consulte [classe SPFeaturePropertyCollection](/previous-versions/office/sharepoint-server/ms461895(v=office.15)).

 Valores de propriedade de recurso idênticos de todos os itens de projeto são mesclados juntos no manifesto de recurso. No entanto, se dois itens de projeto diferentes especificarem a mesma chave de propriedade de recurso com valores não correspondentes, ocorrerá um erro de validação.

 Para adicionar propriedades de recurso diretamente ao arquivo de recurso ( *. Feature*), chame o método de modelo de objeto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Se você usar esse método, lembre-se de que a mesma regra sobre a adição de valores de propriedade de recurso idênticos nas propriedades do recurso também se aplica às propriedades adicionadas diretamente ao arquivo de recurso.

## <a name="feature-receiver"></a>Receptor de recursos
 Os receptores de recursos são o código que é executado quando determinados eventos ocorrem em um recurso que contém um item de projeto. Por exemplo, você pode definir receptores de recursos que são executados quando o recurso é instalado, ativado ou atualizado. Uma maneira de adicionar um receptor de recursos é adicioná-lo diretamente a um recurso, conforme descrito em [passo a passos: Adicionar receptores de evento de recurso](../sharepoint/walkthrough-add-feature-event-receivers.md). Outra maneira é fazer referência a um nome de classe de receptor de recurso e assembly na propriedade **Receiver de recurso** .

### <a name="direct-method"></a>Método direto
 Quando você adiciona um receptor de recursos diretamente a um recurso, um arquivo de código é colocado sob o nó de **recurso** no Gerenciador de soluções. Quando você cria sua solução do SharePoint, o código é compilado em um assembly e implantado no SharePoint. Por padrão, as propriedades do recurso **assembly do receptor** e a **classe Receiver** referenciam o nome da classe e o assembly.

### <a name="reference-method"></a>Método Reference
 Outra maneira de adicionar um receptor de recursos é usando a propriedade **receptor de recurso** de um item de projeto para fazer referência a um assembly de receptor de recurso. O valor da propriedade receiver do recurso tem duas subpropriedades: **assembly** e **nome da classe**. O assembly deve usar seu nome "forte" totalmente qualificado e o nome da classe deve ser o nome completo do tipo. Para obter mais informações, consulte [Assemblies com nome forte](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100)). Depois de implantar a solução no SharePoint, o recurso usa o receptor de recursos referenciado para manipular eventos de recurso.

 No momento da compilação da solução, os valores de Propriedade do receptor de recursos no recurso e seus projetos se mesclam para definir os atributos ReceiverAssembly e ReceiverClass do elemento Feature no manifesto do recurso do arquivo de solução do SharePoint ( *. wsp*). Portanto, se os valores de propriedade assembly e nome de classe de um item de projeto e um recurso forem ambos especificados, o item de projeto e os valores de propriedade de recurso deverão corresponder. Se os valores não corresponderem, você receberá um erro de validação. Se você quiser que um item de projeto faça referência a um assembly de receptor de recursos diferente daquele que seu recurso usa, mova-o para outro recurso.

 Se você fizer referência a um assembly do receptor de recursos que ainda não está no servidor, você também deverá incluir o próprio arquivo de assembly no pacote; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] não a adiciona para você. Quando você implanta o recurso, o arquivo de assembly é copiado para o [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] do sistema ou para a pasta bin no diretório físico do SharePoint. Para obter mais informações, consulte Como: [Adicionar e remover assemblies adicionais](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Para obter mais informações sobre receptores de recursos, consulte [receptor de eventos de recurso](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) e eventos de [recurso](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14)).

## <a name="project-output-references"></a>Referências de saída do projeto
 A propriedade de referências de saída do projeto especifica uma dependência, como um assembly, que o item do projeto precisa executar. Por exemplo, suponha que sua solução tenha um projeto do BDC e um projeto de classe. Se o projeto do BDC tiver uma dependência no assembly que é apresentado pelo projeto de classe, você poderá fazer referência ao assembly na propriedade de referências de saída do projeto do projeto do BDC. Quando o projeto do BDC é empacotado, o assembly dependente é incluído no pacote.

 As referências de saída do projeto geralmente são assemblies, mas em alguns casos (como projetos do Silverlight) podem ser outros tipos de arquivo.

 Para obter mais informações, consulte [como: adicionar uma referência de saída de projeto](../sharepoint/how-to-add-a-project-output-reference.md).

## <a name="safe-control-entries"></a>Entradas de controle seguro
 O SharePoint fornece um mecanismo de segurança, chamado entradas de controle seguro, para limitar o acesso de usuários não confiáveis a determinados controles. Por design, o SharePoint permite que usuários não confiáveis carreguem e criem páginas ASPX no servidor do SharePoint. Para impedir que esses usuários adicionem código não seguro a páginas ASPX, o SharePoint limita seu acesso a *controles seguros*. Os controles seguros são controles ASPX e Web Parts designados como seguros e que podem ser usados por qualquer usuário em seu site. Para obter mais informações, consulte [etapa 4: adicionar sua Web Part à lista de controles seguros](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12)).

 Cada item de projeto do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tem uma propriedade chamada **entradas de controle seguro** que tem duas subpropriedades boolianas: **seguras** e **seguras contra script**. A propriedade Safe especifica se os usuários não confiáveis podem acessar um controle. A propriedade Safe contra script especifica se os usuários não confiáveis podem exibir e alterar as propriedades de um controle.

 As entradas de controle seguro são referenciadas em uma base de assembly. Você adiciona entradas de controle seguro ao assembly de um projeto inserindo-as na propriedade de **entradas de controle seguro** do item de projeto. No entanto, você também pode adicionar entradas de controle seguro ao assembly de um projeto por meio da guia **avançado** no **Designer de pacote** ao adicionar um assembly adicional ao pacote. Para obter mais informações, consulte [como: marcar controles como controles seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md) ou [registrar um assembly de Web Part como um controle seguro](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

### <a name="xml-entries-for-safe-controls"></a>Entradas XML para controles seguros
 Quando você adiciona uma entrada de controle seguro a um item de projeto ou ao assembly do projeto, uma referência é gravada no manifesto do pacote no seguinte formato:

```xml
<Assemblies>
    <Assembly Location="<assembly name>.dll"
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>
        <SafeControls>
            <SafeControl Assembly="<assembly name>.dll" Namespace=
              "<SharePoint project name>" Safe="<true/false>"
                TypeName="<control name>"
                SafeAgainstScript="<true/false>" />
        </SafeControls>
    </Assembly>
</Assemblies>
```

## <a name="see-also"></a>Consulte também
- [Empacotar e implantar soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Usar módulos para incluir arquivos na solução](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [Estender o empacotamento e a implantação do SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
