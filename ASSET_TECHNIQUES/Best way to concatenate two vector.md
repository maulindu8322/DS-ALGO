[Read this](https://stackoverflow.com/questions/3177241/what-is-the-best-way-to-concatenate-two-vectors).

Or you may apply,

      AB.reserve( A.size() + B.size() ); // preallocate memory
      AB.insert( AB.end(), A.begin(), A.end() );
      AB.insert( AB.end(), B.begin(), B.end() );
