---
title: '&lt;serviceCertificate&gt; di &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 3bd6d392b15c37e22fd2a3639c99396e0e3d1749
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750869"
---
# <a name="ltservicecertificategt-of-ltservicecredentialsgt"></a>&lt;serviceCertificate&gt; di &lt;serviceCredentials&gt;
Specifica un certificato X.509 che verrà usato dai client per autenticare il servizio tramite la modalità di sicurezza dei messaggi.  
  
 \<system.ServiceModel>  
\<i comportamenti >  
\<serviceBehaviors>  
\<comportamento >  
\<serviceCredentials>  
\<elemento serviceCertificate >  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<serviceCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`findValue`|Stringa che contiene il valore da cercare nell'archivio certificati X.509. Il tipo contenuto in questo attributo deve soddisfare i requisiti del valore X509FindType specificato. Il valore predefinito è una stringa vuota.|  
|`storeLocation`|Specifica il percorso dell'archivio certificati X.509 usato dal client per convalidare il certificato sul server. Di seguito vengono elencati i valori validi:<br /><br /> -LocalMachine: l'archivio certificati assegnato al computer locale.<br />-CurrentUser: l'archivio certificati assegnato all'utente corrente.<br /><br /> L'impostazione predefinita è LocalMachine.|  
|`storeName`|Specifica il nome dell'archivio certificati X.509 da aprire. Di seguito vengono elencati i valori validi:<br /><br /> -AddressBook: Archivio certificati per altri utenti.<br />-AuthRoot: Archivio certificati per autorità di certificazione di terze parti (CA).<br />-CertificateAuthority: Archivio certificati per autorità di certificazione intermedie (CA).<br />-Disallowed: Archivio certificati per certificati revocati.<br />-My: Archivio certificati per certificati personali.<br />-Root: Archivio certificati per autorità di certificazione radice attendibili (CA).<br />-TrustedPeople: Archivio certificati per utenti e risorse direttamente attendibili.<br />-TrustedPublisher: Archivio certificati per autori direttamente attendibili.<br /><br /> L'impostazione predefinita è My.|  
|`x509FindType`|Definisce il tipo di ricerca X.509 da eseguire. Di seguito vengono elencati i valori validi:<br /><br /> -FindByThumbprint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-   FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Il tipo contenuto nell'attributo `findValue` deve soddisfare i requisiti del valore X509FindType specificato.<br /><br /> L'impostazione predefinita è FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Specifica la credenziale da usare nell'autenticazione del servizio e le impostazioni relative alla convalida delle credenziali client.|  
  
## <a name="remarks"></a>Note  
 Questo elemento consente di specificare il certificato X.509 usato dai client per autenticare il servizio tramite la modalità di sicurezza Messaggio. L'identificazione personale di un certificato che viene rinnovato periodicamente viene anch'essa aggiornata periodicamente di conseguenza. In questo caso, poiché il certificato può essere rilasciato nuovamente con lo stesso nome del soggetto, usare quest'ultimo come tipo `x509FindType`.  
  
 Per ulteriori informazioni sull'utilizzo dell'elemento, vedere [procedura: specificare i valori di credenziale Client](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>  
 [Procedura: Specificare valori di credenziali client](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [Comportamenti di sicurezza](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
