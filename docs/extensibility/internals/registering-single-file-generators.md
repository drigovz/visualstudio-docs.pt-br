---
title: Registrando geradores de arquivos únicos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cea2ebba4739695393447a36e9842ade1670954
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705805"
---
# <a name="registering-single-file-generators"></a>Registrando geradores de arquivo único
Para disponibilizar uma ferramenta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]personalizada, você deve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registrá-la para instancia-la e assoá-la a um tipo específico de projeto.

### <a name="to-register-a-custom-tool"></a>Para registrar uma ferramenta personalizada

1. Registre a ferramenta personalizada DLL no registro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] local ou no registro do sistema, sob HKEY_CLASSES_ROOT.

    Por exemplo, aqui estão as informações de registro da ferramenta personalizada MSDataSetGenerator gerenciada, que vem com: [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Crie uma chave de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registro na colmeia desejada em Geradores\\*GUID* onde *guid* é o GUID definido pelo sistema ou serviço de projeto do idioma específico. O nome da chave torna-se o nome programático da sua ferramenta personalizada. A chave de ferramenta personalizada tem os seguintes valores:

   - (Padrão)

        Opcional. Fornece uma descrição fácil de usar da ferramenta personalizada. Este parâmetro é opcional, mas recomendado.

   - CLSID

        Obrigatórios. Especifica o identificador da biblioteca de classe do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>componente COM que implementa .

   - GeraDesignTimeSource

        Obrigatórios. Indica se os tipos de arquivos produzidos por esta ferramenta personalizada são disponibilizados para designers visuais. O valor deste parâmetro precisa ser (zero) 0 para tipos não disponíveis para designers visuais ou (um) 1 para tipos disponíveis para designers visuais.

   > [!NOTE]
   > Você deve registrar a ferramenta personalizada separadamente para cada idioma para o qual deseja que a ferramenta personalizada esteja disponível.

    Por exemplo, o MSDataSetGenerator registra-se uma vez para cada idioma:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]
   @="Microsoft VB Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]
   @="Microsoft C# Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001
   ```

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Implementando geradores de arquivo único](../../extensibility/internals/implementing-single-file-generators.md)
- [Expondo tipos para designers visuais](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Introdução ao objeto BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
