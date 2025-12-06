
// Author: Saraiva
// Mod: Full Traveling Merchant Shop (Adiciona todos os itens raros permanentemente)

// --- Definições de Classes Nativas do Terraria (Obrigatório) ---
const Chest = new NativeClass('Terraria', 'Chest');
const Item = new NativeClass('Terraria', 'Item');
const NPC = new NativeClass('Terraria', 'NPC');
const Main = new NativeClass('Terraria', 'Main');

const SetDefaults = Item['void SetDefaults(int Type)'];
const SetDefaults2 = Item["void SetDefaults(int Type, bool noMatCheck, ItemVariant variant)"];
const SetupShop = Chest['void SetupShop(int type)'];

// --- Hook para Adicionar Itens à Loja ---
SetupShop.hook((original, self, type) => {

	// Chama a função original para que ele adicione os itens padrão do dia (se houver)
	original(self, type);

	let num = 20; // Posição inicial no inventário da loja (slot)
	let item = self.item; // Array de itens na loja

	// Bloco para o Caixeiro Viajante (Traveling Merchant - ID 471)
	if (type == 471) {
        
        // --- Lista Completa de Itens Raros (Adicionados permanentemente) ---
        
        // 1. Acessórios de Informação e Utilidade
		SetDefaults(item[num], 3097); num++; // Compasso
		SetDefaults(item[num], 3096); num++; // Analisador de Forma de Vida
		SetDefaults(item[num], 3098); num++; // Medidor de DPS
		SetDefaults(item[num], 3095); num++; // Cronômetro
		SetDefaults(item[num], 3037); num++; // Sinalizador Celular (Extenso-Pista)
		SetDefaults(item[num], 3036); num++; // Extenso-Grip
		SetDefaults(item[num], 3035); num++; // Misturador de Cimento Portátil
        
        // 2. Armas, Ferramentas e Itens Especiais
		SetDefaults(item[num], 2270); num++; // Arco de Pulso
		SetDefaults(item[num], 3602); num++; // Varinha de Portal
		SetDefaults(item[num], 3108); num++; // Pistola Gatligator
		SetDefaults(item[num], 2421); num++; // Ímã Celestial
		SetDefaults(item[num], 2434); num++; // Cubo de Gelatina (Gelatinous Pillion)
		SetDefaults(item[num], 1987); num++; // Capacete Peddler (Peddler's Hat)
        
        // ... Você pode adicionar mais itens aqui seguindo a mesma estrutura.
	}
});


// --- Hook para Definir Preços dos Itens Adicionados ---
// Garante que todos os itens tenham um valor de compra correto.
SetDefaults2.hook((original, self, type, noMatCheck, variant) => {

	original(self, type, noMatCheck, variant);
	
	switch(type) {
        
        // Itens de 5 Moedas de Ouro (Exemplos)
        case 3097: // Compasso
		case 3096: // Analisador de Forma de Vida
		case 3098: // Medidor de DPS
		case 3095: // Cronômetro
		case 3037: // Sinalizador Celular
        case 3036: // Extenso-Grip
        case 3035: // Misturador de Cimento
        case 1987: // Capacete Peddler
			self.value = Item.buyPrice(0, 5, 0, 0); // 5 Moedas de Ouro
			break;
            
        // Itens de 10 Moedas de Ouro (Exemplos)
        case 2270: // Arco de Pulso
        case 3108: // Pistola Gatligator
        case 3602: // Varinha de Portal
        case 2421: // Ímã Celestial
			self.value = Item.buyPrice(0, 10, 0, 0); // 10 Moedas de Ouro
			break;
        
        // Item de 4 Moedas de Ouro (Exemplo)
        case 2434: // Cubo de Gelatina
			self.value = Item.buyPrice(0, 4, 0, 0); // 4 Moedas de Ouro
			break;
            
        // Se houver itens de outros mods no seu arquivo, mantenha-os aqui.
	}
});
