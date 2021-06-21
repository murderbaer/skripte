# Threads
## Thread erstellen
```C
#include <pthread.h>
void * func(void *arg) {
    User * u = (User *) arg;
}
pthread_t thread;
if(thread_create(&thread, NULL, func, arg) != 0)
    return; // Thread konnte nicht erstellt werden
```

## Thread stoppen
```C
pthread_cancel(thread); // Cancel Thread
pthread_cancel(pthread_self()); // Cancel current Thread
```

## Auf Thread warten
```C
pthread_join(thread, NULL);
```

# Mutex Lock
```C
static pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;
pthread_mutex_lock(&lock);
pthread_mutex_unlock(&lock);
```

# Semaphore
```C
#include <semaphore.h>
static semd_t sem;
if(sem_init(&sem, 0, 0U) == -1) // Erstellt Semaphore mit Wert 0
    return;
sem_post(&sem); // erhöht Semaphore um 1
sem_wait(&sem); // verringert Semaphore um 1. Wenn der Wert 0 ist wird blockiert
int value;
sem_getvalue(&sem, &value);
sem_destroy(&sem);
```

# Speicher
## Reservieren
```C
Message * msg = (Message*) calloc(1, sizeof(Message)); // 0 initialisiert
Message * msg = (Message*) malloc(sizeof(Message)); // nicht initialisiert
if (msg == NULL) // Fehler beim Speicher reservieren
    return -1; 
```

## Freigeben
```C
free(msg);
```

# Netzwerk
## Port öffnen
```C
#include <sys/socket.h>
int fd = socket(AF_INET, SOCK_STREAMm 0);
if (fd == -1) {
    close(fd);
    return;
}
struct sockaddr_in address;
memset(&address, 0, sizeof(address));
address.sin_family = AF_INET;
address.sin_port = htons(port);
address.sin_addr.s_addr = INADDR_ANY;
if(bind(fd, (struct sockaddr *)&address, sizeof(address)) == -1)
    return; // close

if(listen(fd, backlog) == -1)
    return: // close
```

## Verbindung annehmen
```C
const int sock = accept(passiveSocket, NULL, NULL);
if(sock == -1)
    return; // Error accepting a connection
```

## Daten empfangen
```C
uint64_t number;
ssize_t received = recv(sock, &number, sizeof(number), MSG_WAITALL);
if(received != (ssize_t)sizeof(number))
{
    close(sock);
    return;
}
```

## Daten senden
```C
if (send(sock, &data, sizeof(data), MSG_WAITALL) != (ssize_t)sizeof(data))
    return -1; // es konnte nicht geschickt werden
```

# Daten kopieren
```C
#include <stdio.h>
#include <string.h>

char dest[50];
strcpy(dest, "Heloooo!!"); // copy whole string
strncpy(dest, "Heloooo!!", 5); // copy max 5 bytes
memcpy(dest, src, strlen(src)+1); // copy memory
```

# Message Queue
```C
#include <mqueue.h>

struct mq_attr attr;
attr.mq_flags   = 0;
attr.mq_maxmsg  = 10;
attr.mq_msgsize = sizeof(Message);
attr.mq_curmsgs = 0;

mqd_t messageQueue = mq_open("/queue", O_CREAT | O_RDONLY, 0644, &attr);
mqd_t messageQueue2 = mq_open("/queue", O_WRONLY);
if (messageQueue < 0) // messageQueue konnte nicht geöffnet werden
    return -1;

struct timespec timeout;
timeout.tv_sec = timeout.tv_nsec = 0;
int res = mq_timedsend(messageQueue, (char*)buffer, sizeof(Message), 0, &timeout);
if (res < 0) // MessageQueue full
    return -1;
int res = mq_send(messageQueue, (char*)buffer, sizeof(Message), 0); // blocks if message queue is full

mq_close(messageQueue);
mq_unlink("/queue");
```