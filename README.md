# Louder

Rend plus forts les sons trop faibles : mémos vocaux et musique.

Tu déposes un fichier audio, Louder monte le volume, rapproche les passages chuchotés des passages forts, empêche la saturation, et te donne un fichier WAV à télécharger.

Tout se passe dans le navigateur : le fichier n'est envoyé sur aucun serveur.

## Utilisation

1. Télécharge `index.html` (ou tout le dépôt) et ouvre-le dans Chrome, Firefox, Edge ou Safari.
2. Glisse ton enregistrement dans la zone « Dépose ton fichier audio ici » (ou clique pour le choisir).
3. Vérifie le type de son (**Voix** ou **Musique**, deviné automatiquement), puis choisis la puissance : **Normal**, **Fort** ou **Très fort**.
4. Compare avec les boutons **Original** / **Amplifié**, puis clique sur **Télécharger le fichier amplifié**.

Formats acceptés : MP3, M4A (mémos vocaux iPhone), WAV, OGG, OPUS (WhatsApp), FLAC, WEBM, et la piste audio des vidéos MP4. Les fichiers `.amr` de certains vieux téléphones ne sont pas lus par les navigateurs : convertis-les d'abord en MP3.

## Ce que fait le traitement

| Étape | Rôle |
| --- | --- |
| Passe-haut 80 Hz | Retire les grondements (vent, manipulation du micro, ronflement électrique) qui empêchent de monter le volume. |
| Mise à niveau | Mesure le niveau moyen de la voix en ignorant les silences et le ramène à une référence. |
| Réduction du bruit de fond | Expandeur doux : baisse le son entre les phrases pour ne pas amplifier le souffle. |
| Compression | Réduit l'écart entre les mots faibles et les mots forts. |
| Limiteur | Monte au niveau choisi (voix à −20, −16 ou −12,5 dBFS) et bloque les crêtes à −1 dBFS : aucune saturation. |

En mode **Musique**, le passe-haut 80 Hz et la réduction du bruit de fond sont désactivés (les basses et les passages calmes sont gardés), la compression est plus lente et le niveau visé plus haut (−14, −11 ou −8,5 dBFS). Un morceau du commerce tourne déjà autour de −10 dBFS : il ne peut gagner que quelques dB avant de saturer. Le résultat n'est jamais moins fort que l'original.

Le fichier produit est un WAV 16 bits, 44,1 kHz, mono si l'original l'était.
