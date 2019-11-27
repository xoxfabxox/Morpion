import itertools


def win(jeux_en_cour):

    def all_same(l):
        if l.count(l[0]) == len(l) and l[0] != 0:
            return True
        else:
            return False

    # horizontal
    for ligne in game:
        print(ligne)
        if all_same(ligne):
            print(f"Player {ligne[0]} Gagne a l'horizontale!")
            return True

    # vertical
    for collone in range(len(game[0])):
        check = []
        for ligne in game:
            check.append(ligne[collone])
        if all_same(check):
            print(f"Player {check[0]} Gagne en Verticale!")
            return True

    # / diagonal
    diags = []
    for idx, reverse_idx in enumerate(reversed(range(len(game)))):
        diags.append(game[idx][reverse_idx])

    if all_same(diags):
        print(f"Player {diags[0]} Gagne en Diagonale!(/)")
        return True

    # \ diagonal
    diags = []
    for ix in range(len(game)):
        diags.append(game[ix][ix])

    if all_same(diags):
        print(f"Player {diags[0]} Gagne en Diagonale!(\\)")
        return True

    return False


def plateau_de_jeux(game_map, player=0, ligne=0, col=0, just_display=False):

    try:
        if game_map[ligne][col] != 0:
            print("Espace occuper ! Essaye ailleur")
            return False

        print("   "+"  ".join([str(i) for i in range(len(game_map))]))
        if not just_display:
            game_map[ligne][col] = player
        for count, ligne in enumerate(game_map):
            print(count, ligne)
        return game_map
    except IndexError:
        print("Erreur: Assure toi que Ligne et Colonne sont à 0, 1 ou 2. --> (IndexError)")
        return False
    except Exception as e:
        print(str(e))
        return False


play = True
players = [1, 2]
while play:
    game = [[0, 0, 0],
            [0, 0, 0],
            [0, 0, 0]]

    game_won = False
    player_cycle = itertools.cycle([1, 2])
    plateau_de_jeux(game, just_display=True)
    while not game_won:
        current_player = next(player_cycle)
        played = False
        while not played:
            print(f"Player: {current_player}")
            col_choice = int(input("Colonne ? "))
            ligne_choice = int(input("Ligne? "))
            played = plateau_de_jeux(game, player=current_player, ligne=ligne_choice, col=col_choice)

        if win(game):
            game_won = True
            again = input("Patie terminer ! Voulez-vous rejouer ? (y/n) ")
            if again.lower() == "y":
                print("redémarrage!")
            elif again.lower() == "n":
                print("A bientot !")
                play = False
            else:
                print("réponse invalide, mais a bientot !")
                play = False
