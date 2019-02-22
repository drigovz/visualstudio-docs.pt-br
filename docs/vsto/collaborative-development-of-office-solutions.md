---
title: Desenvolvimento colaborativo de soluções do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 76c26a110d88d3dee8bf7540647ea0bfde4e7c4f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635053"
---
# <a name="collaborative-development-of-office-solutions"></a>Desenvolvimento colaborativo de soluções do Office
  Vários desenvolvedores podem trabalhar em um projeto do Office da mesma forma que eles colaboram em outros projetos do Visual Studio. Visual Studio localiza corretamente a instalação do Microsoft Office em cada computador, mesmo se o Office é instalado em locais diferentes. No entanto, há algumas considerações importantes a serem consideradas.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>Depurar propriedades não são compartilhadas.
 Depurar propriedades não são compartilhadas entre vários usuários sob controle do código-fonte. Projetos Visual Basic e Visual c# armazenam propriedades de depuração em um arquivo específico do usuário (*NomeDoProjeto*. vbproj ou *ProjectName*. csproj), e esse arquivo não está sob controle do código-fonte. Se mais de uma pessoa está depurando, cada pessoa deve inserir manualmente as propriedades de depuração.

 Se o projeto está hospedado em um compartilhamento de rede em vez de no controle de origem, algumas etapas adicionais devem ser executadas para ativar os desenvolvedores de colaboração abrir a solução e o assembly de teste.

## <a name="source-control-requires-checking-out-all-files"></a>Controle de origem requer o check-out de todos os arquivos
 Se você usar o controle do código-fonte para seus projetos, você deve conferir todos os arquivos em um arquivo de código em **Gerenciador de soluções** (como o *ThisDocument*, *ThisWorkbook*, ou *ThisAddIn* arquivos de código) sempre que você alterar o arquivo de código, até mesmo os arquivos que estão ocultos por padrão. Se você fazer check-out apenas o arquivo de código de nível superior, suas alterações poderão ser perdidas.

 Depois de fazer suas alterações, verifique todos os arquivos novamente. Para obter mais informações sobre arquivos de código oculto em projetos, consulte [projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="security-for-informal-collaboration-on-a-network"></a>Segurança para a colaboração informal em uma rede
 Para todas as soluções de nível de documento que estão em um local de rede (como \\ \\ *Servername*\\*Sharename*), o local totalmente qualificado deve ser adicionado ao lista de pastas confiáveis no aplicativo do Microsoft Office que você está trabalhando. Selecione a opção para incluir subdiretórios na pasta principal, ou especificamente adicione debug e criar pastas à lista de pastas confiáveis. Para obter mais informações sobre como fazer isso, consulte [conceder confiança a documentos](../vsto/granting-trust-to-documents.md).

 Os certificados temporários que são gerados automaticamente no momento do build não são protegidos por senhas. Os certificados contêm o nome de logon do desenvolvedor e outras informações pessoais. Se você implantar personalizações que são assinadas por certificados temporários, outras podem ser capazes de acessar essas informações.

## <a name="see-also"></a>Consulte também
- [Proteger as soluções do Office](../vsto/securing-office-solutions.md)
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
- [Compilar soluções do Office](../vsto/building-office-solutions.md)
