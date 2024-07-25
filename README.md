# Orientações Personalizadas

Bem-vindo à Automatize! Este documento foi criado para ajudar você a configurar as stacks para utilizar os serviços hospedados no seu próprio servidor.
## Stacks

Aqui você encontrará todas as stacks pré-configuradas, precisando apenas de alguns ajustes específicos. Cada stack tem sua própria complexidade, então é importante entender um pouco sobre as configurações da aplicação para configurá-la corretamente. Dentro de cada stack, você verá um guia simples para preencher conforme o ambiente do seu servidor (IP, domínios, recursos, etc).

### Configurando a Stack

#### Subindo a Stack

**Checklist para validar a stack antes de fazer o deploy no Portainer:**

**Configurações de Pastas**
- ☑️ **Mapeie os dados corretamente.** Configure os volumes para que a aplicação salve os dados em uma pasta externa, evitando a perda de dados ao atualizar a stack ou reiniciar o servidor.
- 🚨 **IMPORTANTE:** Consulte a documentação oficial se tiver dúvidas sobre alguma configuração específica.
- 🚨 **ATENÇÃO:** Cada aplicação tem um ou mais diretórios a serem mapeados. Para stacks não listadas aqui, consulte a documentação oficial para garantir a configuração correta.

-------------------------------------
CONFIGURAÇÕES REMOVIDAS POR BREVIDADE
-------------------------------------

volumes:
   - redis_insight_data:/db #PASTA A SER SALVA NO DIRETORIO MAPEADO

-------------------------------------
CONFIGURAÇÕES REMOVIDAS POR BREVIDADE
-------------------------------------

volumes:
  redis_insight_data:
    external: true
    name: redis_insight_data



Configurações de rede
☑️ Sempre mantenha as aplicações na mesma rede do Docker para que as aplicações possam se comunicar corretamente.

-------------------------------------
CONFIGURAÇÕES REMOVIDAS POR BREVIDADE
-------------------------------------

networks:
     - academy_network #NOME DA REDE UTILIZADA NAS STACKS ANTERIORES

-------------------------------------
CONFIGURAÇÕES REMOVIDAS POR BREVIDADE
-------------------------------------

networks:
  academy_network:  # NOME DA REDE UTILIZADA NAS STACKS ANTERIORES
    name: academy_network # NOME DA REDE UTILIZADA NAS STACKS ANTERIORES
    external: true 



Possui acesso por subdominio?
☑️ Verifique se o endereço do domínio no traefik está correto

traefik.http.routers.redis_insight.rule=Host(`subdominio.SEUDOMINIO.com.br`


☑️ Verifique se o pameamento da porta da aplicação no traefik está correta.

Exemplo: traefik.http.services.redis_insight.loadBalancer.server.port=5001


☑️ Faça a configuração do subdominio no Cloudflare. 
☑️ Não esqueça de deixar o PROXY desabilitado

Limitando acesso aos recursos da VPS
☑️ Configure o máximo de recurso que o aplicativo pode utilizar. Isto evita que a sua VPS trave por ter deixado as aplicações utilizarem toda a máquina.

resources:
    limits:
        cpus: "1" # Define a quantidade de processadores
        memory: 1024M # Define a quantidade de RAM




Resumo
☑️ Configurar mapeamento de pastas
☑️ Configurar mapeamento da rede interna
☑️ Configurar subdomínios no Cloudflare
☑️ Configurar subdomínio no Traefik
☑️ Configurar mapeamento de porta no Traefik
☑️ Configurar limites de recursos da VPS
✅ PRONTO!
Agora que você passou pelo checklist, pode subir a stack no Portainer!
