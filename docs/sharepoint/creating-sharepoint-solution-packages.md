---
title: Criando pacotes de solução do SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b250be3b61cdfc524f049f952f0cf7e65f1c295a
ms.sourcegitcommit: 174c992ecdc868ecbf7d3cee654bbc2855aeb67d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74876058"
---
# <a name="create-sharepoint-solution-packages"></a>Criar pacotes de solução do SharePoint
  Usando o designer de pacote, você pode criar e personalizar pacotes de implantação. Por exemplo, você pode adicionar recursos e itens de projeto do SharePoint, redefinir o servidor IIS, definir escopos de ativação de recursos e identificar dependências de recursos. O designer também gera um manifesto, um arquivo XML que descreve cada pacote.

## <a name="packaging-tools"></a>Ferramentas de empacotamento
 Você pode usar o **Designer de pacote** para personalizar o pacote e gerar o manifesto. Você pode incluir itens de projeto do SharePoint, configurar se o servidor Web deve ser redefinido e definir o tipo de servidor de implantação. Para obter mais informações, consulte [como adicionar e remover recursos e itens para um pacote usando o designer de pacotes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 Como alternativa, você pode usar o **Gerenciador de empacotamento** para modificar os recursos e itens no arquivo de pacote ( *. wsp*). Para obter mais informações, consulte [como adicionar e remover recursos e itens para um pacote usando o Gerenciador de empacotamento](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

 Você pode usar o Visual Studio e o MSBuild para criar arquivos de pacote ( *. wsp*) para implantar sua solução do SharePoint. Esse processo gera os arquivos de manifesto necessários para a implantação do SharePoint. Para obter mais informações, consulte [como: criar um pacote de solução do SharePoint usando tarefas do MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Opções do designer de pacotes
 A tabela a seguir mostra as propriedades que você pode personalizar em pacotes do SharePoint com o **Designer de pacotes**.

|Propriedade do designer de pacote|Descrição da configuração padrão|
|-------------------------------|------------------------------------|
|Name|Necessária. O nome padrão do pacote é definido como *ProjectName*.|
|Redefinir o servidor da|Opcional. Selecione se você deseja reiniciar o servidor Web depois que o arquivo *. wsp* for instalado no servidor do SharePoint.|
|Tipo de servidor de implantação|Opcional. Representa o tipo de servidor que hospeda o pacote. Se não for definido, o padrão será o WebFrontEnd.<br /><br /> ApplicationServer: descreve um servidor que hospeda os serviços do.<br /><br /> WebFrontEnd: descreve um servidor que hospeda sites da Web.|
|Itens na solução|Todos os itens de projeto do SharePoint e recursos que podem ser adicionados ao pacote.|
|Itens no pacote|Opcional. Todos os itens e recursos do SharePoint que você deseja implantar em seu pacote.|

## <a name="configure-the-packaging-process"></a>Configurar o processo de empacotamento
 Depois de desenvolver soluções do SharePoint no Visual Studio, você pode personalizar o modo como os projetos são empacotados.

 A tabela a seguir mostra os dois destinos do MSBuild que você pode usar para personalizar como o arquivo *. wsp* é criado.

|Destino|Descrição|
|------------|-----------------|
|BeforeLayout|O destino que executa tarefas imediatamente antes de os arquivos serem copiados para um diretório intermediário. Você pode modificar os arquivos antes de criar um arquivo de pacote ( *. wsp*).|
|AfterLayout|O destino que executa tarefas imediatamente após os arquivos serem copiados para um diretório intermediário.|

 Para obter mais informações, [como personalizar um pacote de solução do SharePoint usando destinos do MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).

## <a name="packaging-architecture"></a>Arquitetura de empacotamento
 As etapas a seguir ocorrem quando você cria um pacote do SharePoint ( *. wsp*) no Visual Studio.

1. Os recursos e os pacotes são validados para garantir que a estrutura física e semântica do pacote esteja correta.

2. Os recursos, itens de projeto e arquivos de pacote no pacote são enumerados. Arquivos de manifesto para pacotes e recursos são transformados para incluir todas as informações necessárias para implantação e ativação. Os tokens são substituídos pelo valor totalmente qualificado.

3. O destino BeforeLayout do MSBuild personalizável é executado. Você pode criar essa etapa para fazer quaisquer modificações personalizadas no pacote antes que o arquivo *. wsp* seja criado.

4. Os arquivos enumerados são copiados para um diretório intermediário.

5. O destino AfterLayout do MSBuild personalizável é executado. Você pode criar essa etapa para fazer quaisquer modificações personalizadas no pacote antes que o arquivo *. wsp* seja criado.

6. Os arquivos no diretório intermediário são adicionados ao arquivo *. wsp* .

## <a name="package-folder-structure"></a>Estrutura de pastas do pacote
 Quando você empacota seu projeto do SharePoint, um arquivo *. wsp* é criado para você na pasta *SolutionFolder\bin\\\<BuildConfiguration >* . Por exemplo, se sua solução estiver no *C:\Visual Studio 2013 \ Projects\ListDefinition1* e sua configuração de compilação estiver definida como versão, o arquivo *. wsp* estará localizado no *C:\Visual Studio 2013 \ Projects\ListDefinition1\bin\Release*.

## <a name="see-also"></a>Consulte também
- [Como: personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Como adicionar e remover recursos e itens para um pacote usando o designer de pacotes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Como: criar um pacote de solução do SharePoint usando tarefas do MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Como: criar um pacote de solução do SharePoint usando tarefas do MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Como: personalizar um pacote de solução do SharePoint usando destinos do MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
