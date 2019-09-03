## locust: https://locust.io/

    from locust import HttpLocust, TaskSet, task

    class WebsiteTasks(TaskSet):

      def on_start(self):
          self.client.verify = False
          self.client.get("/")
    
      @task
      def parcelas(self):
          self.client.get("/consultar/parcelas/?termo=&pesquisa_avancada=True&cpf_cnpj=&proprietario=Jos%C3%A9+duarte&cns=&matricula=&codigo=&protocolo=&credenciado=&vertice=&sncr=")

      @task
      def credenciados(self):
          self.client.get("/consultar/credenciados/?codigo=FYG&cpf=&nome=&profissao=&uf=&municipio=&orgao=")
        
        
      @task
      def requerimentos(self):
          self.client.get("/consultar/requerimentos/?protocolo=&cpf_cnpj=&proprietario=&cns=&matricula=&codigo=&credenciado=AFA&vertice=&sncr=&numero_processo=")

    class WebsiteUser(HttpLocust):
        task_set = WebsiteTasks
        min_wait = 5000
        max_wait = 15000
