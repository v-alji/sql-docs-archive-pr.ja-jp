---
title: System.Data.dll | で許可されていない型とメンバーMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
author: rothja
ms.author: jroth
ms.openlocfilehash: cd62f6f0a90bd167f20a33f8de749acc982f39b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634563"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>System.Data.dll の許可されない型およびメンバー
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]共通言語統合 (CLR) プログラミングでは、、、、、、 `HostProtectionAttribute` `System.Security.Permissions.HostProtectionResource` `ExternalProcessMgmt` `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading` 、 **sharedstate**、 `Synchronization` 、または `UI` の値を持つ列挙体を指定するを持つ型またはメンバーの使用は禁止されています。 次の表は、ホスト保護属性 (HPA) 値が許可されない System.Data.dll アセンブリのメンバーおよび型を示しています。  
  
> [!NOTE]  
>  この一覧は、サポートされているアセンブリから作成されたものです。 詳細については、「[サポートされている .NET Framework ライブラリ](../clr-integration/database-objects/supported-net-framework-libraries.md)」を参照してください。  
  
|型またはメンバー|HPA 値|  
|--------------------|--------------------|  
|System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteReader()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency..ctor()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Start()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Stop()|ExternalThreading|  
|System.Data.TypedDataSetGenerator|SharedState、Synchronization|  
|System.Xml.XmlDataDocument|Synchronization|  
  
## <a name="see-also"></a>参照  
 [ホスト保護属性と CLR 統合プログラミング](host-protection-attributes-and-clr-integration-programming.md)   
 [Microsoft.VisualBasic.dllで許可されていない型とメンバー](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [mscorlib.dllで許可されていない型とメンバー](disallowed-types-and-members-in-mscorlib-dll.md)   
 [System.dllで許可されていない型とメンバー](disallowed-types-and-members-in-system-dll.md)   
 [System.Core.dll の許可されない型およびメンバー](disallowed-types-and-members-in-system-core-dll.md)  
  
  
