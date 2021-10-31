# EstrelaDaMorte-SqlServer-DIO

## Script para criação do banco de dados do projeto do BootCamp da Digital Innovation One. Onde foi usado o SQL SERVER para a criação do banco de dados.

### SCRIPT PARA CRIAÇÃO DAS TABELAS DO PROJETO ESTRELA DA MORTE

#### INSTRUÇÃO PARA CRIAR A TABELA PLANETAS
#### CREATE TABLE [Planetas]<br>
##### (  
#####    [IdPlaneta] INT NOT NULL ,  
##### 	 [Nome] VARCHAR(50) NOT NULL ,  
##### 	 [Rotacao] FLOAT NOT NULL ,  
##### 	 [Orbita] FLOAT NOT NULL ,  
##### 	 [Diametro] FLOAT NOT NULL ,  
##### 	 [Clima] VARCHAR(50) NOT NULL ,  
##### 	 [Populacao] INT NOT NULL ,  
##### )  
##### GO  
##### ALTER TABLE [Planetas] ADD CONSTRAINT PK_Planetas PRIMARY KEY ([IdPlaneta]);
-----------------------------------------------------------------------------------------------------------------------------------
#### INSTRUÇÃO PARA CRIAR A TABELA DE PILOTOS
#### CREATE TABLE [Pilotos]
##### (
##### 	[IdPiloto] INT NOT NULL ,
##### 	[Nome] VARCHAR(200) NOT NULL ,
##### 	[AnoNascimento] VARCHAR(10) NOT NULL ,
##### 	[IdPlaneta] INT NOT NULL
##### )
##### GO  
##### ALTER TABLE [Pilotos] ADD CONSTRAINT PK_Pilotos PRIMARY KEY ([IdPiloto]) ;  
##### GO
##### ALTER TABLE [Pilotos] ADD CONSTRAINT FK_Pilotos_Planetas FOREIGN KEY ([IdPlaneta])
##### REFERENCES [Planetas] ([IdPlaneta])
---------------------------------------------------------------------------------------------------------------------------------------
#### INSTRUÇÃO PARA CRIAR A TABELA NAVES
#### CREATE TABLE [Naves]  
##### (
#####	[IdNave] int NOT NULL ,
#####	[Nome] varchar(100) NOT NULL ,
#####	[Modelo] varchar(150) NOT NULL ,
#####	[Passageiros] int NOT NULL ,
#####	[Carga] float NOT NULL ,
#####	[Classe] varchar(100) NOT NULL
##### )
##### GO
##### ALTER TABLE Naves ADD CONSTRAINT PK_Naves PRIMARY KEY (IdNave);
##### GO
-------------------------------------------------------------------------------------------------------------------------------------------
#### INSTRUÇÃO PARA CRIAR A TABELA PILOTOS NAVES<br><br>
#### CREATE TABLE [PilotosNaves]
##### (
#####  [IdPiloto] INT NOT NULL ,
#####  [IdNave] INT NOT NULL ,
#####  [FlagAutorizado] BIT NOT NULL  
##### )
##### GO
##### ALTER TABLE [PilotosNaves] ADD CONSTRAINT [PK_PilotosNaves] PRIMARY KEY ([IdPiloto],[IdNave]);
##### GO  
##### ALTER TABLE [PilotosNaves] ADD CONSTRAINT [FK_PilotosNaves_Pilotos] FOREIGN KEY ([IdPiloto])
##### REFERENCES [Pilotos] ([IdPiloto])
##### GO  
##### ALTER TABLE [PilotosNaves] ADD CONSTRAINT [FK_PilotosNaves_Naves] FOREIGN KEY ([IdNave])
##### REFERENCES [Naves] ([IdNave])
##### GO  
##### ALTER TABLE [PilotosNaves] ADD CONSTRAINT DF_PilotosNaves_FlagAutorizado DEFAULT (1) FOR [FlagAutorizado]
##### GO
--------------------------------------------------------------------------------------------------------------------------------------------
####INSTRUÇÃO PARA CRIAR A TABELA HISTORICO VIAGENS
####CREATE TABLE [HistoricoViagens]
##### (
#####  [IdNave] INT NOT NULL ,
#####  [IdPiloto] INT NOT NULL ,
#####  [DtSaida] DATETIME NOT NULL ,
#####  [DtChegada] DATETIME  NULL
##### )
##### GO

##### ALTER TABLE [HistoricoViagens] ADD CONSTRAINT [FK_HistoricoViagens_PilotosNaves] FOREIGN KEY([IdPiloto], [IdNave])
##### REFERENCES [PilotosNaves] ([IdPiloto], [IdNave])
##### GO
##### ALTER TABLE [HistoricoViagens] CHECK CONSTRAINT FK_HistoricoViagens_PilotosNaves
##### GO
