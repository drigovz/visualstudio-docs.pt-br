---
title: Criando instâncias de projeto usando fábricas de projetos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31ba5dd11af18f8a723b2271544eff2bd292e2e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709059"
---
# <a name="create-project-instances-by-using-project-factories"></a>Criar instâncias de projeto usando fábricas de projetos
Tipos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto em usar uma *fábrica de projetos* para criar instâncias de objetos de projeto. Uma fábrica de projetos é semelhante a uma fábrica de classe padrão para objetos COM cocreatable. No entanto, os objetos do projeto não são cocreatable; eles só podem ser criados usando uma fábrica de projetos.

 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE chama a fábrica de projetos implementada em seu VSPackage quando um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]usuário carrega um projeto existente ou cria um novo projeto em . O novo objeto do projeto fornece ao IDE informações suficientes para preencher o **Solution Explorer**. O novo objeto do projeto também fornece as interfaces necessárias para suportar todas as ações relevantes de interface do usuário iniciadas pelo IDE.

 Você pode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> implementar a interface em uma classe em seu projeto. Normalmente, ele reside em seu próprio módulo.

 Projetos que suportam ser agregados por um proprietário devem persistir uma chave do proprietário em seu arquivo de projeto. Quando <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> o método é chamado em um projeto com uma chave de proprietário, o `CreateProject` projeto próprio converte sua chave de proprietário em uma fábrica de projetos GUID, em seguida, chama o método nesta fábrica de projetos para fazer a criação real.

## <a name="create-an-owned-project"></a>Criar um projeto próprio
 Um proprietário cria um projeto próprio em duas fases:

1. Chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> o método. Isso dá ao projeto próprio a chance de criar um `IUnknown`objeto de projeto agregado com base no controle de entrada . O projeto de `IUnknown` propriedade passa o objeto interno e agregado de volta para o projeto proprietário. Isso dá ao projeto próprio a `IUnknown`chance de armazenar o interior.

2. Chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> o método. O projeto de propriedade faz toda a sua `IVsProjectFactory::CreateProject` instanciação quando este método é chamado em vez de chamar como seria o caso para projetos que não são de propriedade. A `VSOWNEDPROJECTOBJECT` enumeração de entrada é tipicamente o projeto de propriedade agregado. O projeto de propriedade pode usar essa variável para determinar se seu objeto de projeto já foi criado (o cookie não é igual a NULL) ou deve ser criado (cookie é igual a NULL).

   Os tipos de projeto são identificados por um projeto ÚNICO GUID, semelhante ao CLSID de um objeto COM cocreavel. Normalmente, uma fábrica de projetos lida com a criação de instâncias de um único tipo de projeto, embora seja possível ter uma fábrica de projeto lidar com mais de um tipo de projeto GUID.

   Os tipos de projeto estão associados a uma extensão específica do nome do arquivo. Quando um usuário tenta abrir um arquivo de projeto existente ou tenta criar um novo projeto clonando um modelo, o IDE usa a extensão no arquivo para determinar o GUID do projeto correspondente.

   Assim que o IDE determina se ele deve criar um novo projeto ou abrir um projeto existente de um determinado tipo, o IDE usa as informações no registro do sistema em **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]** para descobrir qual VSPackage implementa a fábrica de projetos necessária. O IDE carrega este VSPackage. No <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método, o VSPackage deve registrar sua fábrica de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> projetos com o IDE chamando o método.

   O principal método `IVsProjectFactory` da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>interface é, que deve lidar com dois cenários: abrir um projeto existente e criar um novo projeto. A maioria dos projetos armazena seu estado de projeto em um arquivo de projeto. Normalmente, novos projetos são criados fazendo uma cópia `CreateProject` do arquivo de modelo passado para o método e, em seguida, abrindo a cópia. Os projetos existentes são instanciados pela abertura `CreateProject` direta do arquivo do projeto passado para o método. O `CreateProject` método pode exibir recursos adicionais de iu ao usuário conforme necessário.

   Um projeto também pode usar nenhum arquivo e, em vez disso, armazenar seu estado de projeto em um mecanismo de armazenamento diferente do sistema de arquivos, como um banco de dados ou servidor Web. Neste caso, o parâmetro de nome `CreateProject` do arquivo passado para o método não é realmente um caminho do sistema de arquivos, mas uma seqüência única — uma URL — para identificar os dados do projeto. Você não precisa copiar os arquivos de `CreateProject` modelo que são passados para ativar a seqüência de construção apropriada a ser executada.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Checklist: Crie novos tipos de projetos](../../extensibility/internals/checklist-creating-new-project-types.md)
