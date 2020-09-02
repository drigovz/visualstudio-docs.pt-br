---
title: Registrando geradores de arquivo único | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6afcd708ac50a46ceb3359f0d2c0821e3b788f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696098"
---
# <a name="registering-single-file-generators"></a>Registrando geradores de arquivo único
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para disponibilizar uma ferramenta personalizada no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , você deve registrá-la para que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] possa instanciá-la e o associe a um determinado tipo de projeto.  
  
### <a name="to-register-a-custom-tool"></a>Para registrar uma ferramenta personalizada  
  
1. Registre a DLL de ferramenta personalizada no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Registro local ou no registro do sistema, em HKEY_CLASSES_ROOT.  
  
     Por exemplo, aqui estão as informações de registro da ferramenta personalizada MSDataSetGenerator gerenciada, que vem com [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] :  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2. Crie uma chave do registro no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Hive desejado em GUID de geradores, \\ *GUID* em que *GUID* é o GUID definido pelo serviço ou sistema de projeto do idioma específico. O nome da chave se torna o nome programático de sua ferramenta personalizada. A chave de ferramenta personalizada tem os seguintes valores:  
  
    - (Padrão)  
  
         Opcional. Fornece uma descrição amigável da ferramenta personalizada. Esse parâmetro é opcional, mas recomendado.  
  
    - CLSID  
  
         Obrigatórios. Especifica o identificador da biblioteca de classes do componente COM que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  
  
    - GeneratesDesignTimeSource  
  
         Obrigatórios. Indica se os tipos de arquivos produzidos por essa ferramenta personalizada são disponibilizados para designers visuais. O valor desse parâmetro precisa ser (zero) 0 para tipos não disponíveis para designers visuais ou (um) 1 para tipos disponíveis para designers visuais.  
  
    > [!NOTE]
    > Você deve registrar a ferramenta personalizada separadamente para cada idioma para o qual você deseja que a ferramenta personalizada esteja disponível.  
  
     Por exemplo, o MSDataSetGenerator se registra uma vez para cada idioma:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implementando geradores de arquivo único](../../extensibility/internals/implementing-single-file-generators.md)   
 [Determinando o namespace padrão de um projeto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Expondo tipos a designers visuais](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Introdução ao objeto BuildManager](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
