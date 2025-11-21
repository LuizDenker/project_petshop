create database pet_shop
use pet_shop
create table fornecedor(
ID_Fornecedor INT primary key AUTO_INCREMENT,
Nome_Fornecedor Varchar(100) not null,
Contato VARCHAR(100)
);

create table CLIENTE(
ID_Cliente INT primary key AUTO_INCREMENT,
Nome_Cliente VARCHAR(100) not null,
Telefone VARCHAR(15),
Email VARCHAR(100) UNIQUE
);

create table PET(
ID_Pet INT primary key AUTO_INCREMENT,
Nome_Pet VARCHAR(100) not null,
É_de_Raça BOOLEAN,
ID_Client INT not null,

foreign key (ID_Cliente) references CLIENTE(ID_Cliente)
);

create table ATENDIMENTO(
ID_Atendimento INT primary key AUTO_INCREMENT,
Data_Hora FATATIME not null,
Forma_Pagamento VARCHAR(50),
Pagamento_Aprovado BOOLEAN,

ID_Cliente INT not null,
ID_Funcionamento INT not null,

FOREIGN KEY (ID_Cliente) references CLIENTE(ID_Cliente),
FOREIGN KEY (ID_Funcionario) refrences FUNCIONARIO(ID_Funcionario)
);

create table SERVICO_PRESTADO (
ID_Servico INT primary key AUTO_INCREMENT,
Descricao_Servico  VARCHAR(200) not null,
Valor DECIMAL(10, 2) not null,

ID_Atendimento int not null,
foreign key (ID_Atendimento) refrences ATENDIMENTO(ID_Atendimento)
);

create table ENVIO_FORNECEDOR(
ID_Atendimento INT not null,
ID_Fornecedor INT not null,
Data_Envio Date,

primary KEY(ID_Atendimento, ID_Fornecedor),

foreign key (ID_Atendimento) references ATENDIMENTO(ID_Atendimento),
foreign key (ID_Fornecedor) references FORNECEDOR(ID_Fornecedor)
);
