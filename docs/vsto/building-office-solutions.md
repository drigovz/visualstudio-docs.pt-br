---
title: Criar soluções do Office
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3f89e20b710584c678c035f4d85034e90bb11323
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "69551852"
---
# <a name="build-office-solutions"></a>Criar soluções do Office
  Em geral, compilar e depurar projetos do Office é o mesmo que compilar e depurar outros tipos de projetos no Visual Studio, como Windows Forms. Os tópicos nesta seção explicam as diferenças que existem. Para obter informações gerais sobre como criar aplicativos, consulte [Compilar e compilar no Visual Studio](../ide/compiling-and-building-in-visual-studio.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="project-output-for-office-projects"></a>Saída do projeto para projetos do Office
 O local de saída para projetos do Office é *ProjectName*\bin\Release ou *ProjectName*\bin\Debug. Você não pode criar um diretório de implantação.

### <a name="document-level-projects"></a>Projetos de nível de documento
 Quando você cria um projeto de nível de documento, os seguintes itens são incluídos na saída do projeto:

- Uma cópia do documento do projeto.

- O assembly do projeto e todos os assemblies referenciados que têm sua propriedade **Copy local** definida como **true**.

- O manifesto do aplicativo, que tem a extensão de nome de arquivo *. manifest*. Para obter mais informações, consulte [manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

- O manifesto de implantação, que tem a extensão de nome de arquivo *. vsto*. Para obter mais informações, consulte [manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md).

- Um arquivo de banco de dados do programa (*PDB*).

> [!NOTE]
> Se você criar uma solução em nível de documento para um local remoto em vez do computador local, adicione o caminho totalmente qualificado à lista de locais confiáveis na central de confiabilidade do aplicativo. Para obter mais informações, consulte a seção chamada granting Trust to Documents in [Secure Office Solutions](../vsto/securing-office-solutions.md).

### <a name="application-level-projects"></a>Projetos de nível de aplicativo
 Quando você cria um projeto de suplemento do VSTO, os seguintes itens são incluídos na saída do projeto:

- O assembly do projeto e todos os assemblies referenciados que têm sua propriedade **Copy local** definida como **true**.

- O manifesto do aplicativo, que tem a extensão de nome de arquivo *. manifest*. Para obter mais informações, consulte [manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

- O manifesto de implantação, que tem a extensão de nome de arquivo *. vsto*. Para obter mais informações, consulte [manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md).

- Um arquivo de banco de dados do programa (*PDB*) para o assembly do projeto.

  O processo de compilação para projetos de suplemento do VSTO também cria um conjunto de entradas do registro no computador de desenvolvimento que são necessárias para carregar o suplemento do VSTO. Para obter mais informações, consulte [entradas do registro para suplementos do VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

  Se você criar um projeto de suplemento do VSTO do Outlook que contenha regiões de formulário, o processo de compilação adicionará as seguintes informações adicionais ao registro:

- Uma chave para cada classe de mensagem associada a uma ou mais regiões de formulário.

- Uma entrada para cada região de formulário e um valor associado que representa o nome do suplemento do VSTO do Outlook.

  O Outlook precisa dessas informações para carregar as regiões do formulário.

## <a name="referenced-assemblies"></a>Assemblies referenciados
 Você pode referenciar assemblies (incluindo projetos de biblioteca de classes) de seu projeto de soluções de compilação do Office. Cada assembly referenciado tem uma propriedade chamada **Copy local**. **Copy local** indica se o assembly é copiado para o diretório de saída. Por padrão, ele é definido como **true**. Cada assembly referenciado que tem a **cópia local** definida como **true** é copiado para o diretório de saída.

## <a name="security-during-the-build-process"></a>Segurança durante o processo de compilação
 O Visual Studio configura automaticamente as configurações de segurança no computador de desenvolvimento para conceder confiança à solução durante o processo de compilação. Isso permite que a solução seja executada enquanto você a depura.

 Os projetos do Office usam certificados para verificar o Publicador. O Visual Studio cria automaticamente um certificado temporário para identificar as soluções do Office e configura o computador de desenvolvimento para confiar no certificado temporário.

 Para obter mais informações, consulte [proteger soluções do Office](../vsto/securing-office-solutions.md).

### <a name="network-projects"></a>Projetos de rede
 Se o assembly ou o local do documento estiver em um compartilhamento de rede, a atualização da política de segurança local (nível de usuário) não será suficiente para permitir que a solução seja executada. Um administrador deve conceder confiança total no nível do computador a assemblies e documentos que estão em um compartilhamento de rede antes que a solução seja executada. Para obter mais informações sobre como definir a política de segurança, consulte [proteger soluções do Office](../vsto/securing-office-solutions.md).

 Para projetos de nível de documento, você também deve adicionar o local totalmente qualificado do documento à lista de pastas confiáveis do Office. Para obter mais informações, consulte [Grant Trust to Documents](../vsto/granting-trust-to-documents.md).

## <a name="change-the-platform-target"></a>Alterar o destino da plataforma
 Por padrão, o destino da plataforma para projetos do Office é **qualquer CPU**. Normalmente, você não deve alterar essa configuração. As soluções do Office criadas com qualquer configuração de destino de plataforma de **CPU** são executadas nas versões de 32 bits e 64 bits da Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou do [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] .

 Você deve definir o destino da plataforma como x64 somente se estiver criando uma solução que será executada somente nas versões de 64 bits da Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] e sua solução chamará as APIs nativas de 64 bits. Para obter mais informações sobre como alterar a configuração de destino de plataforma, consulte [como configurar projetos para plataformas de destino](../ide/how-to-configure-projects-to-target-platforms.md).

 Se você definir o destino da plataforma como x64, a solução não será executada nas versões de 32 bits do Windows ou do Office. O destino da plataforma x64 requer que a solução seja executada em um processo de 64 bits.

## <a name="use-the-clean-command"></a>Usar o comando limpar
 Para remover os arquivos de projeto criados do computador de desenvolvimento, você pode usar o comando **limpar** no menu **Compilar** no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . O comando **limpar** exclui todos os arquivos no local de saída da compilação. Para projetos de nível de aplicativo, o comando **limpar** também remove as entradas do registro que são criadas pelo processo de compilação.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Depurar projetos do Office](../vsto/debugging-office-projects.md)|Apresenta os problemas envolvidos na depuração de projetos do Office.|
|[Walkthrough: criar sua primeira personalização em nível de documento para o Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Demonstra como criar uma personalização básica no nível do documento para o Excel.|
|[Como: reabilitar um suplemento do VSTO que foi desabilitado](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Descreve como reabilitar um suplemento do VSTO que tenha sido rígido ou desabilitado por software.|
|[Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)|Fornece links para informações sobre como criar soluções do Office e sobre a função de assemblies em sua solução.|